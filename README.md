# utl-python-pop-up-window-entry-to-create-sas-macro-variable-to-subset-sashelp-class
Using a python pop up window entry to create sas macro variable to subset sashelp class 
    %let pgm=utl-python-pop-up-window-entry-to-create-sas-macro-variable-to-subset-sashelp-class;

    Using a python pop up window entry to create sas macro variable to subset sashelp class

     program Flow
        1  Using python pop up window entry to create macro variable with values M or F
        2. Use the macro variable from python, M or F to subset saselp.class

    related repos on the end

    /*               _     _
     _ __  _ __ ___ | |__ | | ___ _ __ ___
    | `_ \| `__/ _ \| `_ \| |/ _ \ `_ ` _ \
    | |_) | | | (_) | |_) | |  __/ | | | | |
    | .__/|_|  \___/|_.__/|_|\___|_| |_| |_|
    |_|
    */

    /**************************************************************************************************************************/
    /*                               |                                                 |                                      */
    /*         INPUT                 |      PROCESS (MIXTURE OF PYTHON AND SAS)        |      OUTPUT                          */
    /*                               |                                                 | USER ENTERS M then SUBMIT            */
    /*                               |                                                 |                                      */
    /* SASHELP.CLASS to obs=19       |  /*---- Make macro variaable with M or F ----*/ |  +---+---------------+               */
    /*                               |  %utl_submit_py64_310('                         |  |tk        | - [] X |               */
    /* NAME    SEX AGE HEIGHT WEIGHT |  from tkinter import *;                         |  +---+---------------+               */
    /*                               |  import pyperclip as pc;                        |  |                   |               */
    /* Alfred   M   14  69.0   112.5 |  def show_entry_fields():;                      |  | sex(M/F)  M___    |               */
    /* Alice    F   13  56.5    84.0 |  .  print(e1.get(), e2.get());                  |  |                   |               */
    /* Barbara  F   13  65.3    98.0 |  master = Tk();                                 |  |[SUBMIT]           |               */
    /* Carol    F   14  62.8   102.5 |  Label(master, text="Sex(M/F)").grid(row=0);    |  +-------------------+               */
    /* Henry    M   14  63.5   102.5 |  e1 = Entry(master);                            |                                      */
    /* James    M   12  57.3    83.0 |  e1.grid(row=0, column=1);                      |  NAME    SEX AGE HEIGHT WEIGHT       */
    /* ....                          |  Button(master                                  |                                      */
    /*                               |    , text="Apply"                               |  Alfred   M   14  69.0   112.5       */
    /*                               |    , command=master.quit).grid(row=3            |  Henry    M   14  63.5   102.5       */
    /*                               |    , column=0, sticky=W, pady=4);               |  James    M   12  57.3    83.0       */
    /*                               |  mainloop( );                                   |  Jeffrey  M   13  62.5    84.0       */
    /*                               |  mf=e1.get();                                   |  John     M   12  59.0    99.5       */
    /*                               |  pc.copy(mf);                                   |  Philip   M   16  72.0   150.0       */
    /*                               |     ',return=mf);                               |  Robert   M   12  64.8   128         */
    /*                               |                                                 |  Ronald   M   15  67.0   133.0       */
    /*                               |  /*---- Use macro variaable from python  ----*/ |  Thomas   M   11  57.5    85.0       */
    /*                               |  proc print data=sashelp.class                  |  William  M   15  66.5   112.0       */
    /*                               |     (where=(sex="&mf"));                        |                                      */
    /*                               |  run;quit;                                      |                                      */
    /*                               |                                                 |                                      */
    /**************************************************************************************************************************/
    /*                   _
    (_)_ __  _ __  _   _| |_
    | | `_ \| `_ \| | | | __|
    | | | | | |_) | |_| | |_
    |_|_| |_| .__/ \__,_|\__|
            |_|
    */
    /*************************************************************************************************************************/
    /*                                                                                                                       */
    /* +-------------------+                                                                                                 */
    /* |tk        | - [] X |                                                                                                 */
    /* +---+---------------+                                                                                                 */
    /* |                   |                                                                                                 */
    /* | sex(M/F)  M___    |                                                                                                 */
    /* |                   |                                                                                                 */
    /* |[QUIT] [SHOW]      |                                                                                                 */
    /* +-------------------+                                                                                                 */
    /*                                                                                                                       */
    /*                                                                                                                       */
    /*  SASHELP.CLASS to obs=19                                                                                              */
    /*                                                                                                                       */
    /*  NAME    SEX AGE HEIGHT WEIGHT                                                                                        */
    /*                                                                                                                       */
    /*  Alfred   M   14  69.0   112.5                                                                                        */
    /*  Alice    F   13  56.5    84.0                                                                                        */
    /*  Barbara  F   13  65.3    98.0                                                                                        */
    /*  Carol    F   14  62.8   102.5                                                                                        */
    /*  Henry    M   14  63.5   102.5                                                                                        */
    /*  James    M   12  57.3    83.0                                                                                        */
    /*                                                                                                                       */
    /*  THE USER ENTERED M THEN APPLY                                                                                        */
    /*                                                                                                                       */
    /*                                                                                                                       */
    /*                                                                                                                       */
    /*                                                                                                                       */
    /**************************************************************************************************************************/

    /*
     _ __  _ __ ___   ___ ___  ___ ___
    | `_ \| `__/ _ \ / __/ _ \/ __/ __|
    | |_) | | | (_) | (_|  __/\__ \__ \
    | .__/|_|  \___/ \___\___||___/___/
    |_|
    */

     /*---- Make macro variaable with M or F ----*/
     %utl_submit_py64_310('
     from tkinter import *;
     import pyperclip as pc;
     def show_entry_fields():;
     .  print(e1.get(), e2.get());
     master = Tk();
     Label(master, text="Sex(M/F)").grid(row=0);
     e1 = Entry(master);
     e1.grid(row=0, column=1);
     Button(master
       , text="SUBMIT]"
       , command=master.quit).grid(row=3
       , column=0, sticky=W, pady=4);
     mainloop( );
     mf=e1.get();
     pc.copy(mf);
        ',return=mf);

     /*---- Use macro variaable from python  ----*/
     proc print data=sashelp.class
        (where=(sex="&mf"));
     run;quit;

    /**************************************************************************************************************************/
    /*                                                                                                                        */
    /*  NAME    SEX AGE HEIGHT WEIGHT                                                                                         */
    /*                                                                                                                        */
    /*  Alfred   M   14  69.0   112.5                                                                                         */
    /*  Henry    M   14  63.5   102.5                                                                                         */
    /*  James    M   12  57.3    83.0                                                                                         */
    /*  Jeffrey  M   13  62.5    84.0                                                                                         */
    /*  John     M   12  59.0    99.5                                                                                         */
    /*  Philip   M   16  72.0   150.0                                                                                         */
    /*  Robert   M   12  64.8   128                                                                                           */
    /*  Ronald   M   15  67.0   133.0                                                                                         */
    /*  Thomas   M   11  57.5    85.0                                                                                         */
    /*  William  M   15  66.5   112.0                                                                                         */
    /*                                                                                                                        */
    /**************************************************************************************************************************/

    /*        _       _           _
     _ __ ___| | __ _| |_ ___  __| |  _ __ ___ _ __   ___  ___
    | `__/ _ \ |/ _` | __/ _ \/ _` | | `__/ _ \ `_ \ / _ \/ __|
    | | |  __/ | (_| | ||  __/ (_| | | | |  __/ |_) | (_) \__ \
    |_|  \___|_|\__,_|\__\___|\__,_| |_|  \___| .__/ \___/|___/
                                              |_|
    */

    REPO
    ------------------------------------------------------------------------------------------------------------------------------
    https://github.com/rogerjdeangelis/utl-intergrating-interactive-python-popup-checkboxes-with-sas-using-pyqt4-and-tkinter
    https://github.com/rogerjdeangelis/utl_interactive_checkbox_input_using_python_tkinter_to_subset_sas_dataset
    https://github.com/rogerjdeangelis/utl_interactive_input_to_load_a_specified_web_table_into_wps_sas
    https://github.com/rogerjdeangelis/utl_interactive_menu_driven_job_submission_pmenu
    https://github.com/rogerjdeangelis/utl_interactive_text_box_to_set_type_and_length_for_text_file_input
    https://github.com/rogerjdeangelis/utl_sas_python_interactive_checkbox_input_to_sas

    /*              _
      ___ _ __   __| |
     / _ \ `_ \ / _` |
    |  __/ | | | (_| |
     \___|_| |_|\__,_|

    */
