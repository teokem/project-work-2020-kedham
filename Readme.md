The analysis was performed using QIIM2 API.

1. Installing QIIME2(detail information is stated in qiime2.org)
2. Get the table.qza and rep.qza using Qiime2 command line interface. Then import the file to work on Jupyter notebook.
3. Sample metadata (mapping file)
    • Metadata provides the key to gaining biological insight from your raw data. It is a mapping file for the data. The   
      sample metadata used here is available as a google sheet and Keemei is used to validate it. 
    • Open Google drive, then go to My Drive, and click on Blank spreadsheet under Google Sheets. Then Open a file and upload  
      a file from your computer.
    • In order to validate using Keemei: make a copy of the file (by clicking file and then make copy…) in the google 
      spreadsheet. Then click Keemei that is found under Add-ons and validate qiime2 mapping file.
    • Although there is no standard set of criteria for the sample metadata, please check the following link to see the 
      minimum requirements. https://docs.qiime2.org/2020.02/tutorials/metadata/ 
    • In this analysis the sample metadata information was originally imported as CSV or txt file from Illumina-Basespace and 
      converted into TSV file using google spread sheet and saved as sample-metadata.tsv (saved in the analysis working 
      directorate)
    • It is also possible to modify the sample metadata, for instance adding new column or deleting a column (take an example 
      of sample metadata from QIIME2 homepage)

4. Obtaining and Importing sequenced data into QIIME2
   Data produced by QIIME 2 exist as QIIME 2 artifacts. A QIIME 2 artifact typically has the .qza file extension when output   
   data stored in a file. Visualizations are another type of data (.qzv file) generated by QIIME 2, which can be viewed using 
   a web interface https://view.qiime2.org. Since QIIME 2 works with artifacts instead of data files (e.g. FASTA files), we 
   must create a QIIME 2 artifact by importing our fastq.gz data files.

   Format description:
    • Since we have already demultiplexed fastq sequence data, we use Casava 1.8 paired-end demultiplexed fastq to import the 
      data.
    • In the Casava 1.8 paired-end demultiplexed fastq format, there are two-fastq.gz file for each sample in the study, and  
      the file name includes the sample identifier.
    • The forward and reverse read file names for a single sample might look like KHH37-1_S1_L001_R1_001.fastq.gz and 
      KHH37-1_S1_L001_R2_001.fastq.gz, respectively. The underscore-separated fields in this file name are the sample 
      identifier, the barcode sequence or a barcode identifier, the lane number, the read number, and the set number.
    Obtaining data:
    • Using the link available from the sequencing facility downloaded the sequenced file from illumina BaseSpace. Save the  
      file in your computer or on server.
    • Put all fastq.gz file from all samples under one folder rather than keeping them in a separate folder for each sample.  
      Rename the folder as follows: casava-18-paired-end-demultiplexed
     
 
5. Make a summary of imported demultiplexed data
    • Importing the demultiplexed paired-end data, it will give us a QIIME artifact called demux-paired-end.qza. It is useful 
      to generate a summary of the imported demultiplexed data.
      
      Note: 
      At a high level, DADA2 uses PHRED scores to inform an error model. Deblur deviates from this and instead uses a static  
      error model. As a result, DADA2 is potentially better able to accommodate run specific errors. The benefit of a static 
      error model though is that it potentially reduces study bias; the use of a static model was an important criteria for 
      Qiita, the American Gut Project and the Earth Microbiome Project as these efforts are focused around meta-analysis.
      
    - At this stage, you will have artifacts containing the feature table and corresponding feature sequences. You can 
      generate summaries of those as follows.
