---
title: "DPKG issue"
date: 2008-02-21
forum: Installation &amp; Upgrades
---

### Post by delilahjed44 on 2008-02-21
Hey everyone, was looking to install wine through automatix, when I was looking at my notes and saw that it can be installed in synaptic, I started to cancel and this popped up first..

 PHP has changed

 lib php-adodb is no longer installed in /usr/share/adodb new installation path is now /usr/share/php/adodb

 then my bad, to stop the loading I shut the system down.

 Proceeded to start it back up then go into synaptic package manager and cant get in there because of this error
  
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

 I cannot get inot synaptic at all now?

 I dont know how to manually install any to the request above, how do I manually install dpkg? where and how? what is the path? I was trying to install wine to run some programs of mine...

Thank you my OS is Ubuntu 710 Gutsy Gibbon...

Thanks boy I can really goof things up.

Sherri

---

### Post by Pumalite on 2008-02-21
At the Terminal:
sudo dpkg --configure -a

---

### Post by delilahjed44 on 2008-02-21
> **Pumalite said:**
> At the Terminal:
sudo dpkg --configure -a

Hye Pumilite, thank you for saving my butt, you always do and I appreciate it, I am not sure exactly what to do here, should I just chance this and go through the prompts, as I dont know what this is about my sql server deal?

thanks here is what I am receiving.



To properly configure the database for torrentflux, it is necessary that  &#9474;  
 &#9474; you also have mysql-server installed.  Unfortunately, this can not be     &#9474;  
 &#9474; done automatically.                                                       &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; If in doubt, you should choose "abort", and install mysql-server before   &#9474;  
 &#9474; continuing with the configuration of this package.  If you choose         &#9474;  
 &#9474; "retry", you will be allowed to choose different answers (in case you     &#9474;  
 &#9474; chose the wrong database type by mistake).  If you choose "ignore", then  &#9474;  
 &#9474; installation will continue as normal.                                     &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; (Note to translators: don't bother translating this message yet, as the   &#9474;  
 &#9474;  text/wording is not stabilized)                                          &#9474;  
 &#9474;               

 An error seems to have occurred while installing the database. If it's    &#9474;  
 &#9474; of any help, this was the error encountered:                              &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; No mysql client to execute. (have you installed mysql-client?             &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; At this point, you have the option to retry or abort the operation. If    &#9474;  
 &#9474; you choose "retry", you will be prompted with all the configuration       &#9474;  
 &#9474; questions once more and another attempt will be made at performing the    &#9474;  
 &#9474; operation. "retry (skip questions)" will immediately attempt the          &#9474;  
 &#9474; operation again, skipping all questions.  If you choose "abort", the      &#9474;  
 &#9474; operation will fail and you will need to downgrade, reinstall,            &#9474;  
 &#9474; reconfigure this package, or otherwise manually intervene to continue     &#9474;  
 &#9474; using it.  If you choose "ignore", the operation will continue, ignoring  &#9474;  
 &#9474; further errors from dbconfig-common.                                      &#9474;  
 &#9474;

---

### Post by Pumalite on 2008-02-21
You were caught in the middle of doing something related to this, so, if you want your apt-get back; go for it.

---

### Post by delilahjed44 on 2008-02-21
> **Pumalite said:**
> You were caught in the middle of doing something related to this, so, if you want your apt-get back; go for it.

 Yes you are right...as always,, I am afraid to try anything without a consultant as I do not want to wreck my Ubuntu, I went back through the prompts and its working, whewww, panic attack, Ok, I am going to see if I can get wine to work in some of my programs, hey Pumalite thank you really, I do appreciate this, had not you entered that code I would still be in a jam...:popcorn:

Thanks again
Sherri

---

### Post by Pumalite on 2008-02-21
You are welcome. Good luck Sherri.

---

