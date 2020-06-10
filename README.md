# UNSW-Mathematical-Biology
HIVTools (NGlyAlign)
#################################
# Files description
#################################


This is the main code folder. It contains the following files:

1. example_NGlyAlignRun.m to execute NGlyAlign with the input fasta file.
2. main_NGlyAlign.m is the main function that takes sequence as fasta format. It allows either of the following options 
	- option 1(default): main_NGlyAlign(inFile)
	  Input fasta file must be aligned as a requirement to compute global scores, conserved anchors and block anchors. 
	- option 2: main_NGlyAlign(inFile,'anchorSelect','single');
	  a)	Input can be aligned or ungapped/unaligned fasta file
	  b)	The parameter 'anchorSelect' is set to value 'single' to specify
	  program to generate only glycosylation block anchors (global scores and conserved anchors are not generated).
	  
	- option 3:main_NGlyAlign(inFile,'anchorSelect','all','setGlobal','true','scoringMatrix',x,'cutoff',y)
	a)	Input fasta file must be aligned.
	b)	'anchorSelect' is set 'all'
	c)	'setGlobal' is set 'true'
	d)	'scoringMatrix' is set to value x where x is the selection of the scoring matrix 'identity' or 'blosum' 
	e)	'cutoff' is set to threshold y, starting from 95 to 100 (when x is set to use 'identity' matrix) or 0 to 0.85 (when x is set to use 'blosum' scoring matrix with entropy)
	
3.  function_generateConservedAnchors.m contains required functions to compute global scores and generate conserved anchors

4.	function_consensusByIdentity.m contains function to compute percentage of identical residue appeared at each position in MSA.

5.	function_generateGBlockAnchors.m contains required functions to identify glycosylation motifs and their positions to generate block anchors.

6.	contains test file Ref_Kerkhof92_aligned_V1.fasta (collected from van den Kerkhof TLGM, Feenstra K, Euler Z, van Gils MJ, Rijsdijk LWE, Boeser-Nunnink BD, et al. HIV-1 envelope glycoprotein signatures that correlate with the development of cross-reactive neutralizing activity. Retrovirology. 2013;10:102. doi:10.1186/1742-4690-10-102.)

The output contains 

1. globalScores.txt 
	global scores (percentage identity or entropy) for each alignment position in MSA.
2. glycosylationPositions.txt
   List of glycosylation indices for each strain in ungapped alignment MSA.
3. NGlyAnchors.txt
   List of anchors to use as an input for Dialign2.

Final step to align variable region requires
	-NGlyAnchors.txt
	-input fasta file
	with two options to run Dialign
	a)	use online version  http://dialign.gobics.de/anchor/submission.php
	b)  Download latest version of Dialign (C++) from (http://dialign.gobics.de/)

	
