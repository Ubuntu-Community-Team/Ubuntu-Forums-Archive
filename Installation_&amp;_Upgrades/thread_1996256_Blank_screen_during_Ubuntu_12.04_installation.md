---
title: "Blank screen during Ubuntu 12.04 installation?"
date: 2012-06-04
forum: Installation &amp; Upgrades
---

### Post by kkantnaik on 2012-06-04
I tried to install Ubuntu 12.04 (64 bit) into my new HP Pavilion G6-1301 TX which comes pre-loaded with Windows 7. I have to make a dual booted system. But when I try to install from Ubuntu DVD the screen goes blank (no cursor) but fan and hard disk are working. I just cant figure out what can be the problem. And yeah my machine comes with AMD Radeon HD 7450M graphics card, could that be the problem for installation.
 
Please Help!!!! badly need to run Ubuntu :( :confused:

---

### Post by wilee-nilee on 2012-06-04
> **kkantnaik said:**
> I tried to install Ubuntu 12.04 (64 bit) into my new HP Pavilion G6-1301 TX which comes pre-loaded with Windows 7. I have to make a dual booted system. But when I try to install from Ubuntu DVD the screen goes blank (no cursor) but fan and hard disk are working. I just cant figure out what can be the problem. And yeah my machine comes with AMD Radeon HD 7450M graphics card, could that be the problem for installation.
 
Please Help!!!! badly need to run Ubuntu :( :confused:

Try the nomodeset option.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

I would boot to the desktop as well, and make sure it runs okay as well, before installing.

You want to resize the windows with its partitioner, and make sure you are not exceeding the primary partition limits. The resize will leave a unallocated space for Ubuntu.

---

### Post by kkantnaik on 2012-06-04
Thanks a lot sir!!! I am successful in running ubuntu. 

Really very very thanks to you :D

---

### Post by wilee-nilee on 2012-06-04
> **kkantnaik said:**
> Thanks a lot sir!!! I am successful in running ubuntu. 

Really very very thanks to you :D

Cool, enjoy. ;)

---

### Post by Jamesmcskeane on 2012-08-01
I had the exact same problem, however I think this only partially fixes the problem.
The  nomodeset appears to let you boot much better but I continued to experience problems with hibernate closing of the lid where the screen would not resume.

In short i just set it all up not to change i.e. do not let the screen turn off, however I am experiencing an intermittent black screen also...

I think it has something to do with the graphics card maybe or some kind of rendering that cause it to go black screen but then come back again....

It is very annoying :s

---

