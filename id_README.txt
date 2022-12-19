Problem Description : 
    Create a plagiarism detection tool that can detect plagiarism between any two given text files

plagiarism_detection_tool  :
        The detector tool accepts two command line arguments: both being the path to the text files.
        In case of plagiarism the program prints 1 as output else 0.
        The detector is built using Bagofwords and Cosine Similarities.
        

    -> Execute the code :
        The detector accepts command line arguments: path to the text files.
        
        command :
                 python <detector name.py> <file_path_1> <file_path_2>

        makefile to run python :
                make FILE1=<file_path_1> FILE1=<file_path_2> run

        example :  following is a example
                make FILE1=1.txt FILE2=2.txt run
                this will inturn run the below command
                python 40194915_detector.py 1.txt 2.txt

    Steps by Step Process :
        * Import Libraries
        * Reading text files
        * Text Preprocessing
        * Calculated Cosine Similarities
        * Classify if plagiarism.

    1 : Import Libraries
            -> The Libraries required are os, re and sys
            ->  sys, os and Regex are used to read command line arguments, deal with the problem of backslash and forwardslash, and text Preprocessing
                repectively


    2 : Reading text files
            ->  Command line arguments are used to get the file paths.
            ->  Files are read using fileoperator.readlines() which returns a list of all the lines present.
            ->  The list is converted into a string using join() 

    3 : Text preprocessing
            Text preprocessing is one the most important step to clean the data.

            - We have create a function get_text_preprocessed() which takes string as a input andd also returns a string with all the following 
            operations performed. Performed operations are lower(), strip() and removing any punctuation.

    4 : Calculated Cosine Similarities
            Create a function levenshtein_dist() that accepts two strings as input and returns a integer that indicates
            the cosine similarities between the files.

            Both files are converted to vectors and cosine similarity is calcuated.
           
                Calcuation of cosine similarity : 
                        1. We create a corpus that has every word present in both the documents and there frequency.
                        2. Dot Product of each word present in corpus is calcuated using the count and total sum is calcuated.
                        3. Magnutide of each file is calcuated seperately and both Magnutides are sumed.
                                Magnitude = square root of sum of squares of all elements in the element

                FORMULA : 
                        Similarity = (A.B) / (||A||.||B||) where A and B are vectors.            
            Core : 
                -> Main idea is to calculate the similarity between two files so that we can Classify if plagiarism exists or not.
                -> If the similarity is high than Threshold we can conclude that the files are copy of each other.
                -> If the similarity is  not high than Threshold we can conclude that the files are not copy of each other
    
    5 : Classify if plagiarism. (th)
            We have created a lambda function classify_plagiarism that returns 1 and 0 if plagiarism is detected or not
            using the Threshold in this case we are using 0.70 ie 70%.
        