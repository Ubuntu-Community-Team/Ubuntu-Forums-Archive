---
title: "Cannot boot into ubuntu in UEFI mode"
date: 2014-02-23
forum: Installation &amp; Upgrades
---

### Post by udinbak on 2014-02-23
Hello,

Hopefully someone can answer this.

I got a new laptop (msi gs70) with windows 8 pre-installed.
After creating the ubuntu 12.04 live usb (previously booting into legacy mode, because otherwise it just wouldn't boot), and installing ubuntu alongside windows 8, I applied boot-repair.
Boot-repair did the job, but I still cannot boot into ubuntu when in UEFI. Same goes if I try and run any ubuntu distribution on live usb.
Whenever I try to boot into ubuntu, screen just goes black and I cannot do anything.

I have tried replacing quiet splash with nomodeset in grub menu, but nothing happens. I have also tried replacing it with just 'text', but screen just keeps turning black.
Fastboot is disabled, Secureboot is disabled, I have tried disabling intel speedstep, no luck.

Anyone has idea why this is happening?

---

### Post by udinbak on 2014-02-23
So, I can enter recovery mode, but when I try to resume boot I get this error message:

"Fake initctl called, doing nothing".

---

### Post by fdrake on 2014-02-23
did you check that your usb files are not corrupted md5 checksum looks ok?
can you boot into the live cd of ubuntu with nomodeset applied to it?

---

### Post by udinbak on 2014-02-23
Yes, also tried with three different usb. And yes I've already tried with nomodeset in live usb mode, no luck.

---

### Post by oldfred on 2014-02-23
Different model MSI.
 MSI UEFI bug work around A75MA-G55 UEFI boot entries disappear 
[http://forum-en.msi.com/index.php?topic=153411.0](http://forum-en.msi.com/index.php?topic=153411.0)
[http://forum-en.msi.com/](http://forum-en.msi.com/)

What cpu and video chip/card do you have. Often boot parameters are required.

 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

---

### Post by udinbak on 2014-02-23
I have already tried to temporarily boot with nomodeset, no result. Same with the live usb.
Tried ubfan1's options all of them, still the same.
When in Uefi mode, i cannot boot into recovery mode.
I have to change it to uefi with csm, and then use acpi_osi=linux and acpi_backlight=vendor
and, when i enter recovery mode, and try to resume the boot, i get
Warning: Fake initctl called, doing nothing

I have Hybrid Nvidia Geforce 765m (I am aware this is a nightmare, also have tried blacklisting nouveau in the options)

Still, one thing which I do not understand is when I use nomodeset text I should still get some information, correct? I get nothing - just black screen.

i am considering completely erasing windows8, but i am not sure i will be able to boot ubuntu in UEFI when i do this.

---

### Post by oldfred on 2014-02-23
What generation Intel chip?

The very newest 4th Gen Intel chips required the newest Ubuntu. Even though a ways from release, 4th gen seems to work better with 14.04.

While Dell, also discusses some common issues with all vendors and Intel chips.
 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)

---

### Post by udinbak on 2014-02-23
Many thanks oldfred for replying.

Yes, it is 4th gen Intel chip.

The whole problem started when I tried to install nvidia drivers on my laptop (which now I regret deeply)
I was able to dual boot into Windows 8/Ubuntu 12.04 with no problem before. Then, I did something very stupid and tried to install nvidia drivers. 
Yes, I disabled nouveau first, I read through all the topics on the hybrid graphic driver problems. After 12.04, I upgraded to 13.10, then later to 14.04 and still the nvidia driver would not kick in (I have tried everything in the threads).
At one point, I was not even able to enter bios (now I can).
After all this nvidia driver mess, I am not able to boot into UEFI. I reinstalled Ubuntu 12.04 (had to boot in legacy mode first, beause the liveusb does not work in USB mode no matter what I try).

Ok, I have one question - if I reinstall Ubuntu now (newest version), and I choose to delete everything including Windows, do you think I will be able to boot in UEFI mode?

Also, do you have any idea why the recovery mode works only in UEFI with csm mode?

---

### Post by oldfred on 2014-02-23
The Dell link says you have to have CSM on even if booting with UEFI, so Intel driver does something. Not sure how that would be related as I thought that BIOS & UEFI were not compatible and nothing from one really worked with the other.

I have always only installed nVidia drive from Ubuntu's repository. Many years ago I had huge issues with a direct download and stopped doing that. Some with the very newest nVidia card or chips may need the nVidia driver from a ppa or nVidia, but Ubuntu is now better at fairly quickly adding stable nVidia drivers to repository.
If changing from nVidia direct download, ppa version or repository verision you must totally houseclean/purge old nVidia version and delete old xorg, so new one is created.
 sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

      
 Haswell improvements thru 2013
[http://www.phoronix.com/scan.php?page=article&item=intel_2013haswell_end&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_2013haswell_end&num=1)

 Intel "Haswell" System 76 Iris Pro Linux Graphics Yield Some Wins Against Windows
[http://www.phoronix.com/scan.php?page=article&item=intel_irispro_linwin&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_irispro_linwin&num=1)
NVIDIA's Linux Driver On Ubuntu Is Very Competitive With Windows 8
[http://www.phoronix.com/scan.php?page=article&item=nvidia_windows8_geforce&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_windows8_geforce&num=1)

---

### Post by udinbak on 2014-02-23
okay, finally i have something!

I installed of ubuntu 13.10, ran boot-repair and it's still not working, but now when I try and boot into ubuntu I get:

Loading initial ramdisk...
and it just gets stuck.

I can get into recovery mode now with no problem.
And when I press resume boot, I am able to login (text mode).
Afterwards when I tried to startx, I got the no screens found. (which I have encountered many times before)

edit: when I did boot-repair, I chose nomodeset to be included in boot. after removing it from the options, I can finally boot into ubuntu.

Thank you oldfred

---

