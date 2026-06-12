---
title: "Cant get ATI drivers to work after upgrade to lucid lynx"
date: 2010-06-02
forum: Installation &amp; Upgrades
---

### Post by Zireth ZH on 2010-06-02
I had ubuntu karmic... i decided to ugrade to lucid today since i had no probs on my home's pc .. for my surprise while installing the updates for lucid i had errors from fglrx.. i dun remember the errors ive searched for the solution but seems that i cant find anybody who has this thing solved or is it that ivent searched well cuz im at work rite now.. kinda busy...

Here are the errors that it gives me when i try to uninstall the drivers.. Ive tried installing the drivers many ways and it seems that i cant get it working.. and now it wont even let me uninstall it ... ive read that its because there are stuff left there ... im lost on this please help me out guys...

backstage@backstage-desktop:~$ sudo apt-get remove fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  fglrx
0 upgraded, 0 newly installed, 1 to remove and 3 not upgraded.
1 not fully installed or removed.
After this operation, 60.0MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 198762 files and directories currently installed.)
Removing fglrx ...
dpkg-divert: mismatch on package
  when removing `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by fglrx'
  found `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: error processing fglrx (--remove):
 subprocess installed post-removal script returned error exit status 2
Processing triggers for ureadahead ...
Errors were encountered while processing:
 fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)
backstage@backstage-desktop:~$

---

### Post by Zireth ZH on 2010-06-02
please help me out guys

---

### Post by GenBattle on 2010-06-02
I've had this same issue. Can't format and reinstall either (appears to be another separate graphics driver issue with the live cd).

Graphics card: Radeon 5770 1GB

---

### Post by Zireth ZH on 2010-06-02
and its not the only problem i got.. whenever i try to install something this fglrx error still pops in ... i got my drivers to work.. although the pc feels kinda slow or its my imagination .. but still im getting the fglrx errors... 

BTW i just tried reinstalling the propietary drivers and did sudo aticonfig --initial -f then i rebooted and it worked...

But still i need to get those errors fixed cuz its not allowing to install anything plus the overall graphic performance is somewhat slow.... please help

---

### Post by Zireth ZH on 2010-06-03
bump

---

### Post by Zireth ZH on 2010-06-03
Jesus christ ati drivers suck balls in here

---

### Post by Zireth ZH on 2010-06-03
jeez im off with this S

---

### Post by donc786 on 2010-06-15
I have the same problem with ati stuff. I guess ati was a bad choice for a card manufacturer.

---

