---
title: "Oracle 11gR2 Install got some linking-errors."
date: 2009-12-18
forum: Installation &amp; Upgrades
---

### Post by ubumdo on 2009-12-18
hi all,

i installed Oracle 11gR2 on fresh/upgraded installation of ubuntu 9.10. 
During Oracle-Installation i got some link errors. I ignored them and succeeded in installation. 
Certain Oracle-tools (lsnrctl, sqlplus,exp) can be called without errors.

Starting GUI to create db with <dbca>  some windows were blank. Specially last windows (Finish-button => create database.). Thats bad !

I think maybe the link-errors could be the problem. 
So can anybody help me with this installation-error during Oracle-Installation ?
Extract from LOGfile:

Thanks a lot 
[RIGHT][LEFT]---------------------------------

[SIZE=2]INFO:  - Linking dg4odbc agent
rm -f /home/oracle/product/11.2.0/rdbms/lib/dg4odbc
gcc -o /home/oracle/product/11.2.0/rdbms/lib/dg4odbc -m64 -L/home/oracle/product/11.2.0/rdbms/lib/ -L/home/oracle/product/11.2.0/lib/ -L/home/oracle/product/11.2.0/lib/stubs/   /home/oracle/product/11.2.0/hs/lib/dg4odbc.o          /home/oracle/product/11.2.0/rdbms/lib/homts.o          -lhgosh11 -lhggcon11 -lhgosh11  -lagtsh -lpthread -lclntsh   `cat /home/oracle/product/11.2.0/lib/sysliblist` -Wl,-rpath,/home/oracle/product/11.2.0/lib -lm    `
INFO: cat /home/oracle/product/11.2.0/lib/sysliblist` -ldl -lm   -L/home/oracle/product/11.2.0/lib 

INFO: /home/oracle/product/11.2.0/lib//libagtsh.so: undefined reference to `nnfyboot'

INFO: collect2: ld returned 1 exit status
make: *** [/home/oracle/product/11.2.0/rdbms/lib/dg4odbc] Fehler 1

INFO: Ausgabe von gestartetem Prozess beenden.
INFO: ----------------------------------
SCHWERWIEGEND: oracle.sysman.oii.oiil.OiilActionException: Error in invoking target 'idg4odbc' of makefile '/home/oracle/product/11.2.0/rdbms/lib/ins_rdbms.mk'. See '/home/oracle/product/11.2.0/install/relinkActions2009-12-18_01-12-58-PM.log' for details.
    at oracle.sysman.oii.oiis.OiisMakeDeps.invokeMakefile(OiisMakeDeps.java:544)
    at oracle.sysman.oii.oiis.OiisMakeDeps.doRelink(OiisMakeDeps.java:621)
    at oracle.sysman.oii.oiis.OiisMakeDeps.doOperation(OiisMakeDeps.java:802)
    at oracle.sysman.oii.oiis.OiisMakeDeps.main(OiisMakeDeps.java:812)[/SIZE]
[/LEFT]
[/RIGHT]

---

### Post by gundogar on 2009-12-24
I had the same issue. What I did was try to guess the location of the button (check a screenshot of an installation document)and click on that area. it worked for my case. If you are still having same problem I think you should give it a go.

---

### Post by Tim Wiffen on 2010-02-16
Before you install run:
ln /usr/bin/basename /bin/basename
 
I tried ln -s /usr/bin/basename /bin/basename but didn't work

---

### Post by magic_din on 2010-02-27
thanks .. it was helpful to get going ... avoiding this warning

---

