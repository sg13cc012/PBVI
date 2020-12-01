# PBVI
 
### Position Based Variant Identification (PBVI) is a method used to identify low-level variants by directly modeling sequencing error from a control dataset. In general, the method includes model buidling by aggregating reads from BAM files and variant calling by using Fishers exact test.
### This repository contains model files and scripts that can be used to detect low-level variants in 11 overgrowth syndrome genes. It also contains custom scripts used to assess sensitivity for this approach.

### 1) Model building
### The model can be generated by modifying the generate_OGPB_model.py. This python script has defined variables where users can modify to define the directory path to BAM files and full path to a BED file. This will create a dataframe of aggregated counts and create an output file MODEL.txt.
### bamfiles = glob.glob('/BAM_FILE_DIRECTORY/*.bam') #CHANGE THIS TO THE DIRECTORY WHERE BAM FILES ARE, this will look for *bam files
### bedfile = 'OGPB_model_location.bed' #CHANGE THIS TO INPUT BEDFILE

### 2) Variant calling
### After step 1 of Model building, PBVI.py can be modified to use the created model to call variants in an input BAM file. This script requires 4 input files: directory of control BAM files, the bed file used to build the model, reference fasta file, and the model file generated from generate_OGPB_model.py. Users can define this by modifying the below variables in the script below.

### bamfiles = glob.glob('/BAM_FILE_DIRECTORY/*.bam') #CHANGE THIS TO THE DIRECTORY WHERE BAM FILES ARE, this will look for *bam files
### bedfile = 'OGPB_model_location.bed' #CHANGE THIS TO INPUT BEDFILE
### fastafile = 'hg19.fa' #CHANGE THIS TO FASTA REFERENCE FILE
### posmodelfile = 'OGPB_model.txt' #CHANGE THIS TO MODEL FILE
