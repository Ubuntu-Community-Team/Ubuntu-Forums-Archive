---
title: "Unable to boot into Feisty after install"
date: 2007-08-30
forum: Installation &amp; Upgrades
---

### Post by ianikeev on 2007-08-30
Hi

I installed winxp on hd0, then installed Ubuntu on hd1 (hd2 is a backup ide drive, the first two are SATA). The installation goes smoothly, but after reboot I still get windows. I tried several recipes from the forums (like find /boot/grub/stage2 etc. from the grub command line). nothing helps. I reinstalled Feisty, indicating that grub should be installed on hd1. It also goes smoothly, but I can use neither Windows boot loader to boot, nor something like Acronis OS Selector. The most I get is either "GRUB   " and silence or "Starting up..." and silence. Several times I got a "Couldn't mount the partition error":

This is all very strange, because I've never had any problems with Ubuntu auto-installing grub menu any time before (heck, I already had Feisty installed).

I just needed to reinstall everything this time (_needed_, it has no connection to either Ubuntu or anything else) and now I'm stuck wiith this...

Any ideas?

Igor

---

### Post by seshomaru samma on 2007-08-30
why did you not install grub to the MBR (hd0) ?


anyway , try [this]("http://users.bigpond.net.au/hermanzone/p9.html")

---

### Post by piotrwoj on 2007-08-30
My english is very bad :((
 
1) grub
2) device (hdNumber) /dev/hdLetterNumber
root (hd0,number)
setup (hdNumber)
quit
update-grub
dd if=/dev/hdLetterNumber of=bootsect.lin bs=512 count=1
and bootsect lin copy to win32 partition and change boot.ini
C:\BootSect.lin="LINUX - UBUNTU kernel 2.6.xx"
-----------------------------------
[Drzwi Warszawa]("http://www.drzwi-warszawa.pl/")
[Drzwi Antywlamaniowe]("http://www.domar.biz.pl/")

---

### Post by ianikeev on 2007-08-30
tried the WinGRUB thing. Boots, but stops at Error26: cannot read the partition :-()

And yes, I tried to install grub to (hd0) initially: it made no difference -- booted straight into windows

---

### Post by ianikeev on 2007-08-30
[QUOTE=piotrwoj;3279914]My english is very bad :((
 
1) grub
2) device (hdNumber) /dev/hdLetterNumber
root (hd0,number)
setup (hdNumber)
quit
update-grub
dd if=/dev/hdLetterNumber of=bootsect.lin bs=512 count=1
and bootsect lin copy to win32 partition and change boot.ini
C:\BootSect.lin="LINUX - UBUNTU kernel 2.6.xx"


Let's see what this does.... But I've tried it from under LiveCD with no success :(

---

### Post by ianikeev on 2007-08-30
Well, I tried what you suggested, and I'm getting the "GRUB   " thing after boot, nothing else :-( Too bad. Thank you for the input anyway

Igor

---

### Post by seshomaru samma on 2007-08-31
> **ianikeev said:**
> tried the WinGRUB thing. Boots, but stops at Error26: cannot read the partition :-()

And yes, I tried to install grub to (hd0) initially: it made no difference -- booted straight into windows

when you installed grub to hd0 , did you get errors?

---

