Main summary

I, data

1, finemapped eQTL (fm-eqtl) and control SNPs

1.1,

in total 328,661 fm-eqtls with PIP score for different tissues obtained.

fm-eqtl mapped within coding gene 3'UTR will be analyzed here, in total:
2298 fm-eqtls from brain tissues (listed bellow) 
656 from blood tissues (listed bellow) 

Brain pool:

fm-eqtl from different brain regions pooled together:

Brain_Amygdala
Brain_Anterior_cingulate_cortex_BA24
Brain_Caudate_basal_ganglia
Brain_Cerebellar_Hemisphere
Brain_Cerebellum
Brain_Cortex
Brain_Frontal_Cortex_BA9
Brain_Hippocampus
Brain_Hypothalamus
Brain_Nucleus_accumbens_basal_ganglia
Brain_Putamen_basal_ganglia
Brain_Spinal_cord_cervical_c-1
Brain_Substantia_nigra

Blood pool:

Whole_Blood
Cells_EBV-transformed_lymphocytes

1.2,
fm-eqtl will be classified based on pip score cutoff of 0.5 in each of brain or blood tissues, specifically, fm-eqtl with pip score >=0.5 in any sub-tissue and for any transcript (one fm-eqtl may corresponds to multiple tissues and transctipts) will be classified as hP, and the rest s lP, as a result:

261 Blood_hP

395 Blood_lP

597 Brain_hP

1701 Brain_lP

1.3,
48442 common SNPs simulated by the SNPsnap webserver will be used as control for comparison with fm-eqtl.

2, RBP binding regions, miRNA binding sites and 3'UTR cis-elements:

RBP eCLIP: 7082734 regions for 76 RBPs in 22 tissue/cell lines, length 50 bp

RBP POSTAR database: 31186943 regions for 171 RBPs in 24 tissue/cell lines, length 20-50 bp	

miRNA binding sites from targescan database (default conserved ) : 165045 sites for 255 miRNAs, length 6-8 bp

3'UTR ciselements from UTRdb database: 54189 sites for 27 elements, length mostly 20-50 bp, few hundreds


II, slightly higher conservation/selection score in fm-eqtl compared with control:

Distribution of conservatio socres and deepsea-logit value for each RBP: 

https://github.com/lalzs1982/Noncoding/blob/master/images/res_Brainhip_scores_distr.pdf


the AUC is 0.56 for balanced dataset

III, Analysis: any enrichment of fm-eqtl within RBP binding regions:

1, enrichment of fm-eqtl on RBP binding and cis-elements, but not in miRNA binding sites:

eCLIP RBPb: https://github.com/lalzs1982/Noncoding/blob/master/images/res.highpip_rbp_broadtiss.eclip.pdf

Postar2 RBPb: https://github.com/lalzs1982/Noncoding/blob/master/images/res.highpip_rbp_broadtiss.postar.pdf

miRNA binding: https://github.com/lalzs1982/Noncoding/blob/master/images/res.highpip_rbp_broadtiss.consmirna_b.pdf

Cis-element: https://github.com/lalzs1982/Noncoding/blob/master/images/res.highpip_rbp_broadtiss.ciselement.pdf

2, overal enrichment signal is significant compared to control:

random sampling of similar number of higher pip SNPs from among control, and use random as control, repeat the analysis using eCLIP data, 1000 times, calculate number of RBPs with eQTL enrichment (FC>=2, raw p < 0.001)

0 simulation with more significant RBP binding sites than real dataset.
  
3, enrichment analysis via region length comparison:

eQTL distribution within in RBP region among total 3UTR regions

https://github.com/lalzs1982/Noncoding/blob/master/images/res.rbp_eqtl_enrich.Methodcomp.commonSNPvsRegs.pdf


IV, Analysis: higher RBP binding feature score in fm-eqtl compared with control:
1, when use deepsea.ref_predictions (reference base RBP binding probability), we can see AUC of 0.6-0.7 when use balanced positive-negative datasets: 

https://github.com/lalzs1982/Noncoding/blob/master/images/res.highpip_rbp_broadtiss.deepseaRBPfeat.feature_imp_refpred.pdf./res.highpip_rbp_broadtiss.deepseaRBPfeat_refpred.AUC

when using orginal data (unbalanced):

https://github.com/lalzs1982/Noncoding/blob/master/images/res.forxgboost.xgb_train_AUC.aucpr_alldeepsea.pdf


the AUC is just 0.5-0.6 for logit, diff of deepsea predictions, or when use high+low PIP as positive together.

V, Analysis, machinelearning for high PIP brain prediction using RBP (POSTAR2) binding feature

1, use all RBP:
for balanced dataset:
https://github.com/lalzs1982/Noncoding/blob/master/images/res.Brainhighpip_rbp_bal.pred.AUC.pdf

https://github.com/lalzs1982/Noncoding/blob/master/images/res.Brainhighpip_rbp_bal.xgb_train_featureImportance.pdf

general consistence between feature importance and DNM overenrichment

the AUC is 0.53 when using unbalanced dataset

2, selected 28 top RBPs with significantly high enriched highPIP eQTLs:
for balanced dataset
https://github.com/lalzs1982/Noncoding/blob/master/images/res.forxgboost.rbp.sel.bal.xgb_train_AUC.aucpr.pdf

high PIP eQTLs binded by at least one of the selected RBPs:


eQTLs	HighPIP/Not	withinRBPbinding/Not

38385 0	0

10057 0	1

379 1	0

218 1	1
 

the AUC is 0.53 when using original dataset (unbalanced)


VI, for conservation scores (CADD, phylop etc.):

the AUC is 0.54 for balanced data


VII. combination of different features for high PIP brain prediction

1, commbination of conservation score and deepsea ref predictions

https://github.com/lalzs1982/Noncoding/blob/master/images/res.Brainhighpip_anno_deepsea_Ref_bal.pred.AUC.pdf
 and the AUC is 0.66 for original data
 
 

