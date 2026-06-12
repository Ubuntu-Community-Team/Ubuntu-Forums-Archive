---
title: "Installation Problems"
date: 2014-03-16
forum: Installation &amp; Upgrades
---

### Post by Rasheed_Saeed on 2014-03-16
Hello,

I am currently having problems with installing Ubuntu 12.04.4 on my netbook (Acer Extensa 5230E) via USB - I have installed Ubuntu before and experienced no problems. 

As always, I downloaded the ISO (32-bit) from the official Ubuntu website and followed their instructions: Universal USB installer, BIOS settings, etc... The problem I am experiencing is when the installation is loading (where the 'dots' change colour); it decides to just "stop" loading and will forever hold that picture. I have used several USBs, downloaded the same ISO several times, used different software for all the USB's, yet it still holds that picture.

Any advice or recommendations welcome.

---

### Post by manngaurav on 2014-03-16
the most common suggestions are check the hashsum.([https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM))

use another usb or a different program to mount the iso , i have had problems with unetbootin, i tried Linux Live Usb Installer(LiLi) it worked for me.

And maybe your machine isn't powerful enough to run ubuntu , try lubuntu. 

by the way have you tried booting through try without installing? or are you directly installing.?

---

### Post by Mark Phelps on 2014-03-16
>  I have installed Ubuntu before and experienced no problems.

Ubuntu 12.04.4 comes with a newer version of the X-server than prior Ubuntu versions, and that could be causing the problem -- due to a possible conflict with the video card.

You should try booting using the USB WITHOUT installing it, and seeing if you can get to a desktop.  IF you can, open a terminal, enter "lspci" (without the quotes), look for the line containing "VGA" -- and post that info back here.

---

### Post by Rasheed_Saeed on 2014-03-30
I have tried Unetbootin and Start-up Disk Creator, for both Ubuntu 12.04 and 13.10, and I still end up with the same problem. I have also tried to simply go onto Ubuntu without installing it but received the same error.

---

### Post by kc1di on 2014-03-30
> **Rasheed_Saeed said:**
> I have tried Unetbootin and Start-up Disk Creator, for both Ubuntu 12.04 and 13.10, and I still end up with the same problem. I have also tried to simply go onto Ubuntu without installing it but received the same error.

try booting with nomodeset parameter.  you can do that by hitting the tab key when ubuntu starts to boot, then hitting the f6 key > select nomodset.
see if it boots that way.  if it does you can install and get the video card drivers you'll need after. 

also if it boots do as Mark Phelps suggested above, so we can see your video card. good luck.

---

