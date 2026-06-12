---
title: "Unable to get past welcome screen in Ubuntu 14.04 installation"
date: 2014-06-06
forum: Installation &amp; Upgrades
---

### Post by kellyjmorris on 2014-06-06
I am trying to install Ubuntu 14.04 LTS (AMD64) on my computer with an AMD64 processor. I have tried downloading the iso and burning it to DVD (and verifying the cheksum) and also using a DVD purchased from On-disk. In both cases, the screen freezes at the installation welcome screen and I'm unable to use the mouse and keyboard. I've tried holding down on keys, including F12, while booting but evrything leads to the same result.

I would appreciate any guidance. kellyjmorris

---

### Post by ubfan1 on 2014-06-07
Try the nomodeset option (F6 when the grub screen is up, that's the "try" or "install" screen, should have instructions at the bottom if it's purple).  If the grub screen is black, then you have a UEFI machine, and will have to edit the grub commands yourself:  Type "e" then move to the line starting with "linux" and move to the end where the "quiet splash" words are.  Add nomodeset in place of these words, and then try install again.  Give us some more information about your machine so we can give some more specific advice.

---

### Post by kellyjmorris on 2014-06-09
My system is as follows:

7.9 GB memory
64-bit AMD FX-8120 Eight-Core Processor x 8

I am trying to install Ubuntu 14.04 LTS in an 845 GB partition (sdb1) on a 1 TB internal hard drive

I am currently running Ubuntu 12.04 LTS on a separate 500 GB internal HD (sda1) on the same computer. I do NOT want to upgrade from 12.04, which has been a very buggy experience, but rather want a clean install on the 1 TB HD with it set in the BIOS as the primary boot option.

I tried F6 and looked at the options there, none of which I understand. Most importantly, everything I do, including the F6 option, eventually takes me to the Welcome screen of the installation window where the mouse and keyboard are disabled. There's no black screen - just the purple one.

---

### Post by kellyjmorris on 2014-06-14
To clarify my last message I was referring to selecting "nomodeset" when I wrote that I had tried "the F6 option." Having selected "nomodeset," I am able to select "Install." This takes me to the Install window's Welcome screen but the result is the same as before: keyboard and mouse are disabled. In fact, it's a bit worse than before in that the Welcome screen is now distorted (i.e. stretched out horizontally).

---

