---
title: "Help needed"
date: 2007-01-09
forum: Installation &amp; Upgrades
---

### Post by wallacethegreat on 2007-01-09
Hi All,

Can anyone help me please. As a Newbie to Ubuntu, I have just installed 6.06 Dapper onto a Seagate 250Gb External HDD over this last weekend, as I do not want to install it onto my systems main HDD to dual boot (this is to prevent my other half wrecking the system completely by getting Ubuntu loaded and not Windows...  as she has less idea of this than I do.)

Anyway once I had finished installing 6.06 it immediately told me that there were a number of upgrades 300 odd?  that were required. I accepted the upgrades and left it to it.

Once completed I was prompted to restart Ubuntu. When I restarted and went into the boot menu to select my External HDD but it did not appear in the list. I reloaded the live CD and my HDD appeared on the Ubuntu desktop so I reformatted the partitions and reinstalled from the live CD. thus returning to 6.06 Live CD version. This succeeded in returning my HDD  to the boot menu.

What have I done wrong? ](*,) 

 Does this mean that I will be unable to get any upgrades to Ubuntu at all?:confused: 

My system is an AMD x64 3800+ With Windows  MCE  2005. 
1GB DDR2 Ram
160GB internal HDD
250GB External HDD (USB 2 self powered) Being used to run Ubuntu
Nvidia Geforce 7300GS grahics card

Any help hints and suggestions to this newbie will be greatly appreciated..

Many thanks in advance
WallaceTheGreat

---

### Post by teaker1s on 2007-01-09
look at these posts
[http://ubuntuforums.org/showthread.php?t=80811&highlight=breezy+external]("http://ubuntuforums.org/showthread.php?t=80811&highlight=breezy+external")

[http://ubuntuforums.org/showthread.php?t=226638&highlight=breezy+external]("http://ubuntuforums.org/showthread.php?t=226638&highlight=breezy+external")

---

### Post by wallacethegreat on 2007-01-09
Many Thanks I'm looking now.

---

### Post by wallacethegreat on 2007-01-09
Ah I read that and managed to get the initial install. The problem is now that I have Ubuntu installed I cannot upgrade as any upgrade removes the USB drive option from the Boot menu.

I cannot see any way around this 

Any further Ideas on the subject very much appreciated.

---

### Post by teaker1s on 2007-01-09
not ever trying an external install i know very little,but when you do a kernel update normally you can always select previous kernel at boot in grub.

working on the above basis you could edit grub so the new kernel entry has same config as previous kernel.

The usb side-i'll be honest if the second paragraph above won't do it, then you would be better asking on both the threads I posted for you:-k

---

