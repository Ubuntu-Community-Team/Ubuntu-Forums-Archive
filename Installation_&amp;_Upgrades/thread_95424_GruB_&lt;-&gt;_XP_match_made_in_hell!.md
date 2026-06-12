---
title: "GruB &lt;-&gt; XP match made in hell!"
date: 2005-11-26
forum: Installation &amp; Upgrades
---

### Post by mvcmac on 2005-11-26
Installing GRUB on a single HD with XP in the first partition (sda1) is an absolute NO-NO. After about a dozen Ubuntu 5.1 re-installs (all the short-cuts to re-install Grub alone listed in several threads did not work!). I am convinced that XP doesn't tolerate messing about with the MBR. Evertime one logs into XP it modifies GRUB and as a result no XP or Linux boot is possible or selectable for that matter. There should be a much STRONGER warning when installing GRUB the first time in Ubunty. The little yes-no click could cost you several hours if not days of frustration! Maybe having Grub in a separate /boot sector works fine, but I'm not ready to dive off that cliff yet. :???:

---

### Post by atoponce on 2005-11-26
I have had no problems with Windows XP on the first partition of the drive, with Ubuntu on the following partitions.  You do have to be very careful modifying the MBR, as you could lose the ability to boot into XP.  However, I can boot into both operating systems with ease.  What problems specifically have you faced?  Did you defrag XP before partitioning and installing Ubuntu?  What is the size of the hard drive?  What steps are you taking during the install process?  Etc.

---

### Post by paddyg on 2005-11-26
I never had any problems installing Grub to the MBR (I've always installed Grub to the MBR in Fedora, Yoper, Hoary and Breezy). I don't think ide or sata may be relevant (I've got both ide and sata with grub on both). Also, i've had systems with and without boot partitions. Grub is known to be a very tolerant bootloader, and it booted (well,.. chainloaded) 3 windows xp's.

I'm not writing this to sound a smartass, but i really trust grub, and i'd ask mvcmac the same questions atoponce has asked, plus what filesystem are you using for ubuntu?

---

### Post by mvcmac on 2005-11-26
The laptop is a Tecra A4 with a 60Gb drive (Fujitsu MHT2060AT). Did a defrag on XP. Made a 10Gb space with partition magic. Did follow the default instructions to install Ubuntu, format ext3 (sda2) as the Linux partition (10Gb) and (sda5) as swap (.5Gb) and clicked "yes" on overwriting the MBR (instead of a manual configuration). ):
Initially all seem fine, you're able to log into XP the first time but then after a full shutdown / reboot into XP never worked. Of course after a re-install of GRUB all is well, until XP shuts down. When it fails the GRUB script just shows the "GRUB Loading stage1.5. " line and keeps power cycling around that. NO F8 / F10 keys or any intervention is possible (except the power key). Only the C key allows you to start the Ubuntu CD's. Did not install Ubuntu 5.1 from a 
DVD (since I can't burn DVDs on this laptop), maybe that's reason?

---

### Post by aysiu on 2005-11-26
I've always installed Grub to the MBR and never had a problem.

---

### Post by mvcmac on 2005-11-26
BTW I did shut-off the anti virus software to check the bootable files as well. Checked most of my XP programs for interference, but didn't find a trace.
Could it be something inside the Toshiba Tecra BIOS?

---

### Post by bwog on 2005-11-26
Or Partition Magic?

In this section you will see only users with problems ofcourse, the rest happily uses the default method of using Grub to boot XP and Ubuntu and whatever they have, honest.

---

### Post by trash on 2005-11-26
[QUOTE=bwog]Or Partition Magic?[/QUOTE]

I've never had problems either and I don't use PM, but a buddy i know who insists on using PM always seems to have issues.

---

### Post by jdong on 2005-11-26
Turn off the BIOS "virus / boot sector protection" features... They really do nothing but mess with useful software nowadays.

---

### Post by paddyg on 2005-11-26
[QUOTE=trash]I've never had problems either and I don't use PM, but a buddy i know who insists on using PM always seems to have issues.[/QUOTE]
Well, I've always used PM, and never had problems. But I don't have a laptop.
[QUOTE=mvcmac]The laptop is a Tecra A4 with a 60Gb drive (Fujitsu MHT2060AT). Did a defrag on XP. Made a 10Gb space with partition magic. Did follow the default instructions to install Ubuntu, format ext3 (sda2) as the Linux partition (10Gb) and (sda5) as swap (.5Gb) and clicked "yes" on overwriting the MBR (instead of a manual configuration). ):[/QUOTE]
BTW, mvcmac, why didn't you use an extended partition for ubuntu? I've always used extended partitions for linux. I mean, sda1 (winxp), sda2 (extended), sda5 (linux -- ext3), sda6 (swap). But strangely you've got an extended swap partition.

---

### Post by carmaa on 2005-11-30
It's really not Grub that is the main problem here, it's XP. It doesn't seem to like that the bootsector doesn't contain it's own loader, and messes it up when XP is executed. Had this problem on my desktop, did 4 reinstalls of ubuntu, all worked fine until I had to do something in XP, after that, grub halted at Loading stage 1.5. The solution for me was installing grub on the disk the ubuntu was on (I have 2 disks, one for xp and one for linux), and boot that one instead of the XP hdd.

---

