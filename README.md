# utl-calulating-the-most-frequent-sales-amount-by-customer-id
Calulating the most frequent sales amount by customer id  

    Calulating the most frequent sales amount by customer id                                                                
                                                                                                                            
    see github                                                                                                              
    https://tinyurl.com/y7top2fl                                                                                            
    https://github.com/rogerjdeangelis/utl-calulating-the-most-frequent-sales-amount-by-customer-id                         
                                                                                                                            
    Inspired by                                                                                                             
    https://tinyurl.com/yb8s8ltz                                                                                            
    https://communities.sas.com/t5/SAS-Programming/select-most-frequent-character-i-e-country-in-each-group-i-e/m-p/517157  
                                                                                                                            
    Summary is multithreaded, compute the mode.                                                                             
                                                                                                                            
    INPUT  (data does not have to be sorted by ID)                                                                          
    ==============================================                                                                          
                                                                                                                            
     WORK.HAVE total obs=7                                                                                                  
                     |  RULES                                                                                               
       ID     SALES  |                                                                                                      
                     |                                                                                                      
      1000     200   |                                                                                                      
      1000     200   |                                                                                                      
      1000     200   | Most frequent 1000, 200                                                                              
      1000     300   |                                                                                                      
                                                                                                                            
      2000     100   |                                                                                                      
      2000     100   | Most frequent 2000, 100                                                                              
      2000     200   |                                                                                                      
                                                                                                                            
                                                                                                                            
    EXAMPLE OUTPUT                                                                                                          
    --------------                                                                                                          
                                                                                                                            
     WORK.WANT total obs=2                                                                                                  
                                                                                                                            
      ID     SALES                                                                                                          
                                                                                                                            
     1000     200                                                                                                           
     2000     100                                                                                                           
                                                                                                                            
                                                                                                                            
    PROCESS (use the mode)                                                                                                  
    =======                                                                                                                 
                                                                                                                            
    proc summary data=have nway;                                                                                            
      class id; ** no need to sort;                                                                                         
      var sales;                                                                                                            
      output out=want(drop=_:) mode=;                                                                                       
    run;quit;                                                                                                               
                                                                                                                            
    OUTPUT                                                                                                                  
    ======                                                                                                                  
                                                                                                                            
     see above                                                                                                              
                                                                                                                            
    *                _              _       _                                                                               
     _ __ ___   __ _| | _____    __| | __ _| |_ __ _                                                                        
    | '_ ` _ \ / _` | |/ / _ \  / _` |/ _` | __/ _` |                                                                       
    | | | | | | (_| |   <  __/ | (_| | (_| | || (_| |                                                                       
    |_| |_| |_|\__,_|_|\_\___|  \__,_|\__,_|\__\__,_|                                                                       
                                                                                                                            
    ;                                                                                                                       
                                                                                                                            
    data have;                                                                                                              
    infile cards;                                                                                                           
    input id sales;                                                                                                         
    cards4;                                                                                                                 
    1000 200                                                                                                                
    1000 200                                                                                                                
    1000 300                                                                                                                
    1000 200                                                                                                                
    2000 100                                                                                                                
    2000 200                                                                                                                
    2000 100                                                                                                                
    ;;;;                                                                                                                    
    run;quit;                                                                                                               
                                                                                                                            
