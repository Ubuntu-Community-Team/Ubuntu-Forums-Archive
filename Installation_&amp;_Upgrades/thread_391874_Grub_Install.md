---
title: "Grub Install"
date: 2007-03-23
forum: Installation &amp; Upgrades
---

### Post by Epis0de on 2007-03-23
Ok, ive spent 6 hours on this, and im ready to throw my computer out the window.

Heres the situation...

- I have one Ubuntu Live CD, which im using at the minute to run my computer.
- I have 2 SATA HD's Raided. I believe the nvidia "thingy" said they were "striped".
- I occasionally am greeted with Error 22, though also ive had it say "grub loading" then spend forever loading nothing, I assume its just hung.
- I have no coffee left.

I am begging, for your assistance, I have a huge amount of Economics coursework that needs to be completed and my head is sore. More importantly, I have no XP bootdisc or available CD-R's :(

/beg

---

### Post by Epis0de on 2007-03-23
Bump for great justice.

---

### Post by Epis0de on 2007-03-23
Anyboddyyyiiee... :(

Help please, totally flustered.

---

### Post by confused57 on 2007-03-23
I don't know if you can make a Win98SE oem boot floppy from the live cd or not:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

I don't have any Raid configurations, but maybe this will help:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

What does this command show from the live cd:
```
sudo fdisk -l
```
the -l is a small "L"

---

### Post by Epis0de on 2007-03-23
Ill try that if this nuclear option (I unplugged a 160gb hard-disc to kill the raid) fails. 

Its says...

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19083   153284166   83  Linux
/dev/sda2           19084       19457     3004155    5  Extended
/dev/sda5           19084       19457     3004123+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 


But I assume that because I just raped the raid and am in the middle of partitioning.

Ill shout back if anything develops.

---

### Post by Epis0de on 2007-03-23
Apparently Ubuntu for some god unknown reason doesnt support DMraid :|

Regardless, ill take any workaround I can get now, then search for a proper solution later. Returning to Windows is not really an option at this point.

---

### Post by confused57 on 2007-03-23
> **Epis0de said:**
> Apparently Ubuntu for some god unknown reason doesnt support DMraid :|

Regardless, ill take any workaround I can get now, then search for a proper solution later. Returning to Windows is not really an option at this point.
What you could try is to install grub to the mbr of your sda, using the live cd(leave your other drive disconnected):
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)
If "find /boot/grub/stage 1" results in "root (hd1,0)", you'd probably "setup (hd1)"?


Once, you have grub installed to the sda mbr, boot up your computer(set sda to boot first in bios)...hopefully this will give you a grub menu at boot...if it does, highlight the Ubuntu entry, press "e" to edit, change your line with root to (hd0,0), then press "b" to boot.  This change is temporary, if it actually works...the changes can be made permanent in your /boot/grub/menu.lst.


If you're able to boot into Ubuntu, you'd be able to make a Win98 boot floppy & repair your mbr.

---

