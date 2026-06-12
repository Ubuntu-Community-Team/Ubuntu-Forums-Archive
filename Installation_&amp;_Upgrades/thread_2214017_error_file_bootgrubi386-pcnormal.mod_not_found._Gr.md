---
title: "error file /boot/grub/i386-pc/normal.mod not found. Grub Rescue &gt;"
date: 2014-03-30
forum: Installation &amp; Upgrades
---

### Post by drhans2 on 2014-03-30
I'm trying to installed Ubuntu 11.10 along side Windows XP on a old E Machine desktop with a 2.40 GHz Pentium 4 CPU with 1 GB ram. Graphic card is NVIDA Getforce FX 5600 Ultra.

Ubuntu would load from the CD to the "Install or Try" screen. If "Trying" the desktop would load to the background screen but nothing else. I was never able to click on anything. I figured it was do to low ram.

I then chose to "Install" Ubuntu and after booting to Ubuntu the Desktop would never load. The only way to get the Desktop screen was to reboot and choose the Ubuntu "recovery mode/resume." then Ubuntu worked.

 I figured I'd try to reinstall Ubuntu to see if that would correct my problem but read some forum notes about problems with the swap file if doing a reinstall.

I chose to just delete the 3 partitions I created earlier and start over. I then chose to just have 2 partitions, Windows & a empty partition for Ubuntu & let Ubuntu "Install to the empty partition along side Windows rather then try to partition the HD again.

After Ubuntu finished installing I rebooted and I got the error message... error file /boot/grub/i386-pc/normal.mod not found. Grub Rescue >

I did search the forum for the problem but most answers were way over my head.

I did look at the disk with G-Parted and the Windows partition is still there along with 2 Ubuntu partitions. I can't find any way to boot into Windows XP or Ubuntu.


That's about much as I can explain the problem... other than...  I clueless as what to do next. Also I'm not familiar with the Linux OS at all.

Any thoughts as what to next?     As a last resort... Is there a fix just to get Windows to boot.

 Much thanks, denny

---

### Post by mörgæs on 2014-03-30
11.10 is out of support. For this old fella I recommend Lubuntu 13.10. 
In a live boot you can open Gparted and remove the failed Ubuntu partitions.

---

### Post by drhans2 on 2014-03-30
Thanks for the reply.. I will try Lubuntu 13.10. I did boot to a older Ubuntu live CD and deleted all partitions other then Windows XP. When I rebooted the computer I then got a error message.. Error: no such partition.  Grub rescue > 

That's not the same results I got the last time I deleted the partitions.. Then I was able to boot to Windows XP.  

Before trying to install Lubuntu I first would like to restore my option to boot to Windows XP if possible. The Windows partition is still there.. along with two unallocated partitions but need to know how to restore the original boot option. Is there a way to edit the grub file with maybe the live CD? 

thanks..

---

### Post by mörgæs on 2014-03-30
After installing Lubuntu you will get the multiboot option automatically.

---

