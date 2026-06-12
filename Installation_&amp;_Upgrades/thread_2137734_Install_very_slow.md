---
title: "Install very slow"
date: 2013-04-21
forum: Installation &amp; Upgrades
---

### Post by allanstuart on 2013-04-21
attempting to install from usb on a nc 10 previously used for XP.The install has been running for 8 hours ,Terminal response is very slow but does respond but light on ethernet socket does a number of flashes at 1 sec intervals and I have response from the toothed wheel which is able to suspend and then resume operation.I have asked to install in tandem with the XP system which I know had two disk partitions but in the initial phase it did not request any input about additional partitions for linux.Should I shut down and what do you think has happened?

---

### Post by oldfred on 2013-04-21
Please do not hijack another thread with a different issue. Boot issues are almost always unique.

How much RAM does you system have?

Years ago I attempted to install Ubuntu into a system that did not have enough RAM and it was very slow like yours. Updates took the same amount of time or overnight. It did boot but I think it was running everything from swap and was as slow as molasses.

If you do not have a lot of RAM then Lubuntu may be better?
       Lubuntu, which uses the LXDE desktop environment, targeted at "normal computers" with 128 MB
With 512Mb of RAM and almost any processor, Lubuntu will perform more than adequately out-of-the box. 
I'd suggest to check amjjawad's thread (Lubuntu One Stop Thread) and you'll find many useful information.
[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)
[https://help.ubuntu.com/community/LubuntuLinks](https://help.ubuntu.com/community/LubuntuLinks)
[http://ubuntuforums.org/showthread.php?t=1844755](http://ubuntuforums.org/showthread.php?t=1844755)
Lubuntu is an Operating System that is using LXDE.
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)
[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

---

### Post by allanstuart on 2013-04-23
Thank you for your reply but in my attempts to improve the situation I managed to destroy the Recovery and C: partitions on my drive.I do not use that notebook for anything vital so using Unetbootin I decided to go for a full installation of Ubuntu.I managed to create a boot usb which does start my computer and completes the language and keyboard tasks but then it fails in the next task ' Searching for installer ISO image'.I created the boot usb by using Unetbootin and the contents of the usb consisted of the following items:- disk, boot, casper, bootex, casper r/w, menu csl, syslinux.cfg, ubinit, ubkern, ubuntu-12.10 desktop. The last item is a zip file which contains 131 items. The parameters I used in running unetbootin were as follows:-
Select distribution=Ubuntu, Option= 12.10 Hdmedia, diskimage = selected.The program completed successfully.
I am hampered by the fact that the notebook is unuseable, my other computer is a Chromebox but I have access to a neighbours PC running Vista please suggest a way forward to implementing Ubuntu on my Samsung notebook .I would appreciate any help you can give me as despite having been working on computers since 1966 I am very much a novice on Linux.
regards Allan

---

### Post by oldfred on 2013-04-23
I think you should download and try the Lubuntu version.

Full Ubuntu is now for higher end systems. The Xubuntu & Lubuntu flavors work just fine on lower end systems, it is just a different desktop.  Part of the issue is that Unity needs a good video system to run well. With my 6 yr old dual core system with 4GB of RAM,  I do not run Unity but run the gnome-panel which uses somewhat less resources.

Did system work in live mode, before you installed?  Sometimes download is not good and it only takes one minor error and install will not work.

You can verify download with md5sum.
       [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

I think it was 1965 that I had first class in programming FORTRAN and Assembly on Illiac II or IBM 3094.

---

### Post by allanstuart on 2013-04-23
just to let you know that my second problem appears to be a corrupt boot file.I recreated another one using unetbootin and did a full install and it all went like a dream.Response is now good and my computer notebook which has a 1,6mhz processor,250mb hdd and 1gb ram performs very well.Thanks for your help and consider this thread closed.:p

---

