---
title: "nvidia-glx upgrade error"
date: 2007-01-15
forum: Installation &amp; Upgrades
---

### Post by gh0st on 2007-01-15
Hi folks,

I have just installed Edgy on my shiny new AMD Dual-Core machine and I can't get Compiz working properly. I installed the nvidia-glx driver and then found out I needed a beta or something to get the visuals working properly.

The guide I read on Lunapark said to add some repos and then upgrade your driver, I followed the instructions and this is what I get in the terminal:

dan@frank:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  nvidia-glx
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

It seems to know the package can be upgraded but doesn't want to do it. What does this mean? "package kept back". Do I have to enter some command to force the upgrade or something? I'm probably making some newbie error :) 

Any help would be gratefully received. Thanks in advance.

---

### Post by Sqwishy on 2007-01-15
when doing a dist-upgrade as adivsed by synaptic
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  nvidia-glx
The following packages will be upgraded:
  linux-restricted-modules-2.6.17-10-generic
1 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.

```
so i have the same problem, going on for about a week now. i'm using amd64 edgy by the way

EDIT:
The problem has gotten worser, i can't upgrade the following packages without removing nvidia-glx!
```
beryl beryl-plugins beryl-settings linux-restricted-modules-2.6.17-10-generic
``` :'(

---

