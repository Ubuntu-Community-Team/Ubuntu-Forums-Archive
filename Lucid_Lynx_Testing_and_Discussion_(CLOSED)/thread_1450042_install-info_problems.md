---
title: "install-info problems"
date: 2010-04-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by vav on 2010-04-08
I can't run any more updates because install-info fails... with the following message:
Errors were encountered while processing:
 install-info
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up install-info (4.13a.dfsg.1-5ubuntu1) ...
 
    Error: You are superuser.
 
           For security reasons superuser is not allowed to start
           the license manager.
 
           Either startup the license manager as a regular user or
           stay as superuser and use the -u option and an alternative
           username. For help use the -h option.
 
dpkg: error processing install-info (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of info:
 info depends on install-info; however:
  Package install-info is not configured yet.
dpkg: error processing info (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on info; however:
  Package info is not configured yet.
dpkg: error processing ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 install-info
 info
 ubuntu-standard



What to do?!

---

### Post by phenest on 2010-04-08
Try...
```
sudo apt-get -f install
```

---

### Post by SevenMachines on 2010-04-08
do you get this when you run 
$sudo update-info-dir
too?
have you installed any recent non-ubuntu packages at all?

{EDIT} Matlab?  [FONT=monospace][/FONT]FLEXlm license manager?

---

### Post by vav on 2010-04-09
Yes! Yes!
I have flexlm installed, and I do get it when I do update-info-dir. How do I tackle this? MATLAB works btw...

Also apt-get -f doesn't work...

---

### Post by SevenMachines on 2010-04-09
sorry, dont really know, i dont use anything that uses flexlm, hopefully someone else knows more. i think /usr/share/info is the directory update-info-dir gets its information so you might want to look into that to see if theres something using flexlm. seems strange though, i wouldnt have thought update-info-dir could result in something like this but there you go

---

