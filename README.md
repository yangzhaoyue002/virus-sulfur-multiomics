# virus-sulfur-multiomics

This repository contains the scripts and workflows used in the study:  

**"Virus-Induced Dominance of Sulfur-Oxidizing Bacteria via Enhanced Substrate Access and Competitor Suppression"**.

It includes complete pipelines for:
- 16S rRNA amplicon processing using QIIME2
- Metagenomic assembly with MEGAHIT
- Metagenome binning using MetaWRAP (MetaBAT2, MaxBin2, CONCOCT), followed by bin classification with GTDB-Tk  
- Viral detection via VirSorter2 and vContact2
- Functional annotation with eggNOG-mapper and hmmsearch against SCycDB
- Gene/contig abundance was estimated using CoverM
- Virus–host prediction using WiSH
- Statistical analysis and visualization using R (vegan, phyloseq, ggplot2)

## How to Run

### Process 16S rRNA amplicon data
bash scripts/16S_qiime2_pipeline.sh

### Assemble metagenomes and identify viral contigs
bash scripts/metagenomic_data_pipeline.sh
bash scripts/virome_data_pipeline.sh

### Generate statistical plots
Rscript analysis/analysis_plot.R

## Main tools and versions
- QIIME2 — 16S rRNA amplicon analysis
- MEGAHIT (v1.2.9) — Metagenomic contig assembly
- MetaWRAP (v1.3.2) — Binning (MetaBAT2, MaxBin2, CONCOCT)
- GTDB-Tk (v2.1.1) — Phylogenomic annotation of bins
- MMseqs2 — Clustering nucleotide contigs
- Prodigal (v2.6.3) — ORF prediction
- eggNOG-mapper (v2) — Functional annotation
- HMMER (v3.3.2) — hmmsearch against SCycDB for sulfur metabolism genes
- VirSorter2 (v2.2.3) — Viral identification
- vContact2 (v0.8.1) — Viral genome classification
- WiSH (v1.1) —  Virus-host association prediction 
- R (v4.4.0) with phyloseq, vegan, ggplot2 — statistics and visualization

## Classifier Resource (for 16S annotation)
This pipeline requires a pretrained classifier for the 16S rRNA V3–V4 region based on the SILVA 138 database.
Please manually download the following files from the [QIIME2 SILVA data resource](https://docs.qiime2.org/2022.8/data-resources/):

- `silva-138-99-seqs.qza`  
- `silva-138-99-tax.qza`

 These files will be used for classifier training and taxonomy assignment in `scripts/16S_qiime2_pipeline.sh`.
