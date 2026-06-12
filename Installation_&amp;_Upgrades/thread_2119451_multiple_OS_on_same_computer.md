---
title: "multiple OS on same computer"
date: 2013-02-23
forum: Installation &amp; Upgrades
---

### Post by ntoprint on 2013-02-23
My laptop currently runs on Windows7 and Ubuntu12.1 . I cannot completely do away with W7 yet, because I am still working on transferring and saving information. But, as of right now, I am running a dual booting system so that both OSs are on this computer.

I have fallen in love with Ubuntu, it is the best, fastest and easiest OS I have ever dealt with. This being said, I have been looking into the Edubuntu for my two daughters. I wanted to know if I could install a 3rd OS on my system?

I installed Ubuntu onto my computer using the Windows download tool and installed it dirrectly onto my computer that way. I was wondering if I could use that same tool and download Edubuntu onto my computer? I want to keep my W7 and U OSs intact. I just wanted to make sure that if I used that Windows downloading tool again, but picked Edubuntu as the OS, that it wouldn't overwrite my Ubuntu OS. 

Advice?

Thanks in advance.

---

### Post by offgridguy on 2013-02-23
Yes you can, there is some info in this thread.

[http://ubuntuforums.org/showthread.php?t=2075214](http://ubuntuforums.org/showthread.php?t=2075214)

It sounds like you used the wubi install, I don't think you can do that for a third 
Operating System.  Better to have each system on it's own partition.
Gparted how to Tutorial here.

[http://dedoimedo.com/computers/gparted.html](http://dedoimedo.com/computers/gparted.html)

Unless your computer is very new with uefi bootloader and gpt partitioning.

---

### Post by ahallubuntu on 2013-02-23
~

---

### Post by kartikrajkanna on 2013-02-23
Um, You could install Edubuntu as an Ubuntu desktop Environment?

```
sudo apt-get install edubuntu-desktop
```

maybe .....

---

### Post by ahallubuntu on 2013-02-23
> **kartikrajkanna said:**
> Um, You could install Edubuntu as an Ubuntu desktop Environment?

```
sudo apt-get install edubuntu-desktop
```

maybe .....

I assumed OP wanted a completely separate OS that the kids could play with and not mess up anything in the Ubuntu install.

---

### Post by kartikrajkanna on 2013-02-23
Ah! I seemed to have missed that point ..... and btw, doesn't Wubi slow down the computer or something like that?

It happened on my laptop ( 8 years old ..... Inspiron 700m: 2 GB RAM. Intel Pentium M 1.60 GHz )

Just Asking. :)

---

### Post by AngJinhang on 2013-02-23
do you have a separated partition for your ubuntu? if yes,that's good.
just download the edubuntu's iso and make a bootable usb drive,and install it. you may see this dialog during the install...
'you currently have windows 7 and ubuntu 12.10 on this system.what do you want to do?'
just choose run alongside them.but, you may end up in seeing two ubuntu in the grub boot menu.
i have tried to install three system on a pc and it worked well.

---

### Post by kartikrajkanna on 2013-02-24
> **AngJinhang said:**
> do you have a separated partition for your Ubuntu?

Um, it says that Ubuntu was installed using Wubi, so no new partition, unless partition tool was used .....

ntoprint, you might wanna get your Ubuntu in a new partition before installing Edubuntu alongside Win7, because Wubi AND Edubuntu might slow your system down.

---

