# utl_more_robust_techniques_for_manipulating_macro_variable_text
More robust techniques for manipulating macro variable text.  Keywords: sas sql join merge big data analytics macros oracle teradata mysql sas communities stackoverflow statistics artificial inteligence AI Python R Java Javascript WPS Matlab SPSS Scala Perl C C# Excel MS Access JSON graphics maps NLP natural language processing machine learning igraph DOSUBL DOW loop stackoverflow SAS community.
    More robust techniques for manipulating macro variable text

    Concatenating macro variables

         Two Solutions

              1. Outside a macro
              2. Inside a macro

    github
    https://tinyurl.com/yd9uu4bz
    https://github.com/rogerjdeangelis/utl_more_robust_techniques_for_manipulating_macro_variable_text

    see
    https://communities.sas.com/t5/Base-SAS-Programming/concatinating-macro-variable/m-p/472764


    The techniques below are more robust because

      %let path= '&&yes%todat/*56555,"; eq not %&oo';

      can be problematic in pure macro code and fails with the solutions provided.



    INPUT
    ======

    Concatenate these

    %let path= '&&yes%todat/*56555,"; eq not %&oo';
    %let file='online.csv' ;

    SOLUTIONS
    =========

    OUTSIDE OF A MACRO
    ------------------

    data _null_;

       res=cats(&path.,&file);
       call symputx('res',res);

    run;quit;

    %put %superq(res);

    &&yes%todat/*56555,"; eq not %&ooonline.csv


    INSIDE MACRO
    --------------

    %macro around(summy);

      %let rc=%sysfunc(dosubl('

        data _null_;

           res=cats(&path.,&file);
           call symputx("res",res);

        run;quit;
      '));

      %put %superq(res);

    %mend around;

    %around;


    &&yes%todat/*56555,"; eq not %&ooonline.csv


