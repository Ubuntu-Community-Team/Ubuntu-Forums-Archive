---
title: "&quot;Unable to install GRUB in /dev/sda&quot; during install"
date: 2014-01-08
forum: Installation &amp; Upgrades
---

### Post by victorcl2 on 2014-01-08
There have been many threads regarding this problem but I have not been able to find a solution to this.

The main problem is that the Ubuntu installation wants to install GRUB in /dev/sda, even when /dev/sdb is selected as the installation drive. An easy fix to this is to disconnect any extra drive; however, in my case, it requires disassembling the laptop which I do not want to do; I have a second drive in a caddy.

When I load the Live USB, /dev/sda is usually the bootable usb drive, or sometimes the caddy.

Is there a way to specify which drive GRUB installs to in the Live USB. Or rename/swap /dev/sdb to /dev/sda?

---

### Post by Bucky Ball on 2014-01-08
Why do you not want it in sda? That is where you would normally put it (unless you already have a Ubuntu install that has its grub in sda, then you would install it in sdb). What do you have on the machine already? Are you attempting to dual-boot with Win or this is Ubuntu only?

There is an option during the install which asks where you would like to put grub. Maybe you missed it.

---

### Post by victorcl2 on 2014-01-08
I do not have any OS on my laptop at the moment. I have a SSD and another drive in a caddy. The SSD is where I want to install Ubuntu; however, it is set to /dev/sdb in the live usb boot. When installing, I usually select the "Erase disk and install" option since I am not dual-booting or anything. I guess I should try the "Something Else" option for manual setup?

---

### Post by Bucky Ball on 2014-01-08
Yep, go 'Something Else'. That let's you choose where to install grub. I understand now. It probably wouldn't matter where it went, you'd still get a boot somehow, but best to stick it on the same drive as your install as it is the only OS, sdb by the sounds. 

With just Ubuntu it should be simple. To keep in mind: if not an EFI install, you are limited to four partitions per physical disk, any combination of primary or extended partitions. 

An extended partition, though, can have any number of logical drives (for all intents and purposes regular partitions) inside it. The extended partition is like a holder for the logical drives (of interest, a Ubuntu install can exist on a logical partition and doesn't need a primary, unlike Win).

For instance:

/ = root, primary;
/extended partition = holder for:
   /home
   /music
   /swap

This would count as two partitions on the drive, / as a primary and /extended being an extended, although for all intents and purposes, there are five, with /home, /music and /swap inside /extended partition. You can add another two partitions, primary or extended, to the physical disk (I usually just put the OS on a primary and everything else inside an extended. At the moment I have about nine logical partitions inside the extended partition on my lappy).

PS: Take the drive in the caddy out and reboot. Still sdb? You could leave the caddy drive out when installing to avoid confusion and any accidental loss of data.

---

### Post by victorcl2 on 2014-01-08
Bucky Ball, manually creating the partitions in "Something Else" worked! Thanks! I did not even have to remove my hard drive caddy either. That was something I really wanted to avoid cause it requires disassembling the laptop.
I will no longer use the "Replace OS with Ubuntu" option from now on if there are other drives connected.

---

### Post by Bucky Ball on 2014-01-08
Great news! Yep, the automagic 'install alongside' route can be problematic, and if you are dual-booting Win8 in EFI, using that option when installing Ubuntu can wipe the drive and install Ubuntu only on the whole drive (it doesn't see the Win partitions so just considers it to be an empty drive). Ouch.

Enjoy! ;)

---

