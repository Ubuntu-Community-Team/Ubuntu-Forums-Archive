---
title: "Trouble after ubuntu instalation"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by dav7mx on 2007-04-27
Hi, I'm new in the forum and I have very little experience with Linux.

The problem is this:
I installed Ubuntu 6.06 LTS in my laptop and everything went ok. I restarted the computer after the installation and I logged in. I moved the pointer and clicked on applications button. It didn't work. I treated to click other things but It seemed the mouse wasn't working. I was able to move the mouse pointer, but I think the computer didn't respond when I clicked something. I turned off  the laptop and tried again. It happened the same, I wasn't able to click anything. 

My laptop is a compaq presario. It's quite old but it works ok. It has 128 RAM, and only 40 Gb of memory (What can I do?, this is the best I can afford :( ) so this may be a problem. What vertion of ubuntu do you recommend me for my computer? (if you need more details about my laptop's characteristics, please ask me). 

I think that there may be a problem with the mouse driver. I have tried to plug a mouse to the lap top, but this didn't work either. 

So, please tell me what can I do, because I can't use anything!!

In the worst of cases, how can I uninstall ubuntu? Can I install other Linux vertion over the partition in which ubuntu is installed? 

I left windows installed just in case something like this happenedHi, I'm new in the forum and I have very little experience with Linux.

The problem is this:
I installed Ubuntu 6.06 LTS in my laptop and everything went ok. I restarted the computer after the installation and I logged in. I moved the pointer and clicked on applications button. It didn't work. I treated to click other things but It seemed the mouse wasn't working. I was able to move the mouse pointer, but I think the computer didn't respond when I clicked on somethig. I turned off  the laptop and tried again. It happened the same, I wasn't able to click anything. 

My laptor is a compaq presario. It's quite old bur it works ok. it has 128 RAM, and only 40 Gb of memory (What can I do?, this is the best I can afford :( ) so this may be a problem. What vertion of ubuntu do you recommend me for my computer? (if you need more details about my laptop's characteristics, please ask me). 

I think that there may be a problem with the mouse driver. I have tried to plug a mouse to the lap top, but this didn't work either. 

So, please tell me what can I do, because I can't use anything!!

In the worst of cases, how can I uninstall ubuntu? Can I install other Linux vertion over the partition in which ubuntu is installed? 

I left windows installed just in case.

Thank you very much for your help..

Thank you very much for your help.

---

### Post by zvacet on 2007-04-28
You are low in RAM and that could be reason why you can not get Dapper work.You can remove ubuntu desktop and instead of it install xubuntu desktop wich is lighter.

**ctrl+alt+F1**

```
sudo aptitude remove ubuntu-desktop
```

```
sudo aptitude install xubuntu-desktop
```

---

### Post by dav7mx on 2007-04-29
Hi, thank  you very much for the answer.

I just discovered something else. When I installed ubuntu, I didn't make any swap partition, basically because I didn't know that I have to. I still don't understand what is the use for this partition. Do I really have to do it? If so, how can I do it? Remember that I only have access to Linux terminal and  to windows. 

zvacet, I tried what you recommended me, but ir seem ir didn't work. During ubuntu-desktop remove there were several errors of the kind: "[07902102.20304059] not enough memory, process 1234 killed nautilus". Is this because I don't have the swap memory? Then I tried to install xubuntu-desktop, and I have an error that said something like: "dpkg stopped. Manually run dpkg --configure -a". When the "installation" finished, I tried to run: $ sude dpkg --configure -a, but the same "not enough memory" error appeared.

So, Is there a way to correct my error and make the swap partition or should I try to install again ubuntu and make the partition? :confused: 

Thanks for your answers.

---

