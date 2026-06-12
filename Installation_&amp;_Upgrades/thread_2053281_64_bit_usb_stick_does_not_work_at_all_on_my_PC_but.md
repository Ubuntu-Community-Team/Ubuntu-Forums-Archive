---
title: "64 bit usb stick does not work at all on my PC but needed due to UEFI ?"
date: 2012-09-05
forum: Installation &amp; Upgrades
---

### Post by szdavid on 2012-09-05
Hello

I bought yesterday HP Pavilion p6-2243ef 
I wanted to install Ubuntu.

Used to it, I took the 32 bits ISO, put it on a USB stick.

The live ubuntu in that case works like a charm and installation, no problem

But when I restart the computer : no choice, windows starts by itself...

I think it is due to UEFI.
Following what I can find on Internet, I wanted to do the same operation with 64 bits but this stick does not work at all 
- in UEFI mode, after choosing "try ubuntu without installing", black screen even with the nomodeset option
- in BIOS mode, when saying try ubuntu, it says me that the graphic card, screen can not be set up (I do not remember the exact wordings), I am trying to validate the screen asking if it is ok : I say yes but it crashes the system or go to a loop "do you want to use low graphics setup or the previous setup" and each time it comes back to this question, whatever I answer....

Two questions : 
- do I miss something in order to be able to start the 64bits stick ? I do not understand why I would be able to start in 32 bits but not in 64, with the same graphic card,....

- To install Ubuntu beside Windws would be the perfect solution but if I disable UEFI and format the full drive, could i install Ubuntu 32bits AND start the OS (today, after the installation of the 32 bits, when I select the hard drive in "BIOS mode" (it is called inherited startup devices in the bios setup), it says "Exiting PXE row ; ERROR no boot disk has been detected or the disk has failed" ; 
Maybe here I missed something in the installation but I am a little bit worried (today at least, I am able to start Windows...)

Thank you for your help !

David

---

### Post by oldfred on 2012-09-06
If you have UEFI and Windows is UEFI, then you have to use the 64bit version of Ubuntu to have to UEFI install option. It should give two choices on booting, one BIOS mode and the other UEFI.

What video card/chip do you have. Often that is a second complication for new systems with UEFI. You may just need the nomodeset option, but some very new systems need other boot options also.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Just saw this from arpanaut's post in another thread.
There is a bug in ubiquity on the 12.04 iso that causes the installer to crash part way through on some hardware.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/996568](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/996568)
From liveCD before install. 
sudo apt-get remove ubiquity-slideshow-ubuntu
or (ubiquity-slideshow-lubuntu) (and ubiquity-slideshow-xubuntu)

---

