LTL commands: 

Question 1: 
To check for all communications in the system, any communication that is started (with a start signal) is finished (with a stop signal)
check_ltlspec -p "G ( (up[0]=start -> F (up[0]=stop)) & (up[1]=start -> F (up[1]=stop)) & (down[0]=start -> F (down[0]=stop)) & (down[1]=start -> F (down[1]=stop)) )"



Question 2: 
To check whether the solution preserves mutual exclusion
check_ltlspec -p "G !( (process1.localkey = TRUE) & (process2.localkey = TRUE) )"

To check that starvation exist in the solution
check_ltlspec -p "G ( F (process1.localkey = TRUE) & F (process2.localkey = TRUE) )"



Question 3: 
To check whether the solution preserves mutual exclusion
check_ltlspec -p "G !( (process0.state = crit) & (process1.state = crit) )"

To check that starvation exist in the solution
check_ltlspec -p "G ( F (process0.state = crit) & F (process1.state = crit) )"
