---
title: "Install 6.10 in IBM Thinkpad 600e"
date: 2007-01-16
forum: Installation &amp; Upgrades
---

### Post by Jeremy07860 on 2007-01-16
Hello

Here I go again, trying to install Ubuntu on an old laptop.  Heres my latest project.

IBM ThinkPad 600E

Upon starting the pc with the Ubuntu disk in the drive, it boots from disk, I select to Run or Install Ubuntu.  The next thing I get is this;

[17179569.184000] ACPI: Vendor "IBM   " System "TP600E   " Revision 0x105 has a known ACPI BIOS problem.
[17179569.184000] ACPI: Reason: Incorrect _ADR.  This is a non-recoverable error
[   129.149291] invalid compressed format (err=2)
[   129.156294] Kernal panic - not syncing: VFS: Unable to mount root fs on unknown-block(1,0)
[    129.156374]  _



Any Ideas... I can get other LiveCD versions of Linux to run... but they suck, I want Ubuntu


-Jeremy

---

### Post by grumpymole on 2007-01-16
Jeremy,

I have seen others have problems with the Live CD and a TP 600E.  I usually go straight for the alternate CD (text-based installer).  This tends to work more reliably across different hardware.

Also, for the 600E, Xubuntu is good to try out.

Regards

Warren
[http://grumpymole.blogspot.com](http://grumpymole.blogspot.com)

---

### Post by rockycmt on 2007-01-17
Jeremy,

I am new to ubuntu.  I tried to install it on my 600E last night and had the same error.  I formatted my HD before I tried the install.  I am going to try the Alt CD install tonight.  Let me know if you make any progress?

Chris

---

### Post by linyutang on 2007-01-26
I am installing Xubuntu in a 600x thinkpad (500 mhz PIII) and have almost the exact same results.  I am getting:
[    48.674871] invalid compressed format (err=1)
[    48.679260] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(1,0)
[    48.679321]

I will try the text input as mentioned earlier... if I can figure it out.

---

### Post by fastbikeboy on 2007-02-07
linyutang,
             I had this same issue and what I did to correct it was update the bios. I did not have floppy drive so I had to make an image from the disk image that you download from IBM's site. Now I have installed kubuntu 6.10 and ubuntu 6.10 perfectly. If you would like this image let me know and I will send it your way. 

Thanks,
fastbikeboy

---

### Post by pseb on 2007-02-08
hi jeremy,
i have ubuntu 6.10 running on an ibm thinkpad 600e. works like a charm.
i recommend to use the alternate install cd und do a server install and then add the software you really need via apt-get (since i have only 64MB ram even xfce is too heavy, so i use icewm).
to install:
disable quickboot in your bios. (maybe you have to initialize the bios BEFORE you disable quickboot). then boot the cd with acpi=off and pnpbios=off. (acpi does not really work, but apm does).
hope it helps,
sebastian

---

