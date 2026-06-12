---
title: "Replace Windows 10 with Ubuntu"
date: 2018-04-15
forum: Installation &amp; Upgrades
---

### Post by mikebr2 on 2018-04-15
Hello all.

I have a two in one Acer tablet that has windows 10.  It has 32 Gb in hard disk and additional 16 Gb as microSD.

It runs on an Atom processor.

I have tried to replace the windows 10 with Ubuntu and even Mint several times, unsuccessfully.

I tried booting from a USB using YUMI, changed the booting order in the DOS prompt {or whatever it is called}. 

I did this several times and the Acer just did not rebooted with the Ubuntu installation menu, as it is supposed to happen.

Really do not know what more to do.

Any advise is appreciated and take in mind I am an average PC user; normal every day language is much appreciated.

Thanks.

---

### Post by yancek on 2018-04-15
Acer requires you to set Trust somewhere in the BIOS before you can install another operating system.  You will need to check your user manual or google it or wait for someone more familiar with Acer.
You need to change the boot priority in the BIOS to usb which may be under HDD option.  MIght show the name of your flash drive.  I think the key to access BIOS is F2 but you should see it at the bottom of the screen when you reboot.

---

### Post by ubfan1 on 2018-04-16
You might need to set a BIOS supervisor password before the "trust" options are offered.

---

### Post by oldfred on 2018-04-16
Some have had to update UEFI from Acer to have settings or have them work.

Trust settings seem to be identical for all models of Acer.
See these where users posted more details on "trust".
 Acer Swift 3
[https://ubuntuforums.org/showthread.php?t=2370998](https://ubuntuforums.org/showthread.php?t=2370998) 
      
 Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[URL="https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742"]https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742
[/URL]
 Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392) 

[URL="https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742"]
[/URL]

---

### Post by leunam12 on 2018-04-16
I don't think you can run Ubuntu on that tablet, what model is it?

---

### Post by ajnadriaan on 2018-04-16
Some tablets are restricted to running 32 bit operating systems only,  even when the processor is 64 bit. Check whether the installed Windows is  32 or 64 bit, and if 32, try again with 32 bit Linux.

---

### Post by Mark Phelps on 2018-04-17
Tablets, like laptops, are notoriously bad at using Linux, due primarily to the shortage of Linux drivers -- so BEFORE you wipe out a working OS on your tablet and turn it into an "electric brick", I strongly suggest you create boot media of the Linux distro you want to use, boot from that and see how well it works on the tablet.

You might luck out -- it might work just fine!  But, if you run into problems, fixing them will range from easy (presuming a Linux driver exists) to impossible (presuming a Linux driver does NOT exist).

---

