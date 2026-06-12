---
title: "los my usc and have problem to install it again"
date: 2012-01-29
forum: Installation &amp; Upgrades
---

### Post by Ax3 on 2012-01-29
Hi  mates

i los my ubuntu sofware center  by mistak  , ans i can't reinstall it , the following mesg appear 

sudo apt-get install software-center
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 software-center : Depends: software-center-aptdaemon-plugins but it is not installable
                   Depends: gir1.2-glib-2.0 (>= 1.31) but 1.30.0-0ubuntu2 is to be installed
                   Depends: python-gi-cairo but it is not installable
                   Depends: python-debtagshw but it is not installable
E: Unable to correct problems, you have held broken packages.

then i tried to reinstall it from synaptic  and frome ubuntu web sit    online  and got the same  mesg 
 i mad  -f instal    and  fix broken backge    and dpkg --configure -a , get nothing also  ..... i reied to dwonload the missing  backeg  i  gor python-gi- cairo  and fall to install it using gdebi  also i can't find the other backg     ,,, 

 i need ur help guys  i want to re install my ubuntu software center  my version is 11.1
thank you

---

### Post by dino99 on 2012-01-29
adding packages from untrusted archives is the best way to get a borked installation: only use genuine ubuntu archives (purge the ppa via synaptic)

---

### Post by Ax3 on 2012-01-29
> **dino99 said:**
> adding packages from untrusted archives is the best way to get a borked installation: only use genuine ubuntu archives (purge the ppa via synaptic)
  thank u i burged all ppa and make down grade then mak restart and sudo apt-get update  , after that i had reinstall USC  successfuly  then restor my PPA by YPPA manger  , and mak update to my system   , but now i have small problem with start up  , it' start up withe balck screen    , ubuntu logo and ubuntu start up screen didn't appear just i have the startup sound  can u kindly help me
 than you again

---

