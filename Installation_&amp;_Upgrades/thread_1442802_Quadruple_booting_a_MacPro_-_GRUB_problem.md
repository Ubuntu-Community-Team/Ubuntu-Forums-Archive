---
title: "Quadruple booting a MacPro - GRUB problem"
date: 2010-03-30
forum: Installation &amp; Upgrades
---

### Post by Robert Elkow on 2010-03-30
Please see my thread entitled Quadruple booting a MacPro for background information.

In that thread I mention that when I boot into Ubuntu other choices come up which include Windows 7 - 64 and Windows xp.  When I use the cursor to boot xp I get the GRUB menu again,  When I use the cursor to boot Windows 7 it works just fine.  I checked the grub.cfg file and compared the command paragraph for Windows 7 and xp.  Except for going to different partitions like what I would expect the xp command paragraph has an additional line:  

drivemap -s (hd0) $ (root)

Can anyone tell me what this means and whether it is causing the problem?

Should it be changed or eliminated?

I attempted to create another entry with this line left out but was not permitted to change the file because it was read only.  How can I change it?

---

### Post by oldfred on 2010-03-30
The drivemap command just switches drives. If root is hd0 it does nothing.

Your windows installs both only boot thru one windows. Windows when installed sets the boot flag. The second windows can only boot thru the first one with the boot flag and windows moves files to that partition. With some work you can separate them if you want.

For a new install workaround:
To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

some of the workarounds:
Way to boot windows in extended logical partition with lilo's MBR
[http://ubuntuforums.org/showthread.php?t=1367323](http://ubuntuforums.org/showthread.php?t=1367323)
Major windows repair with dual boot and logical partition
[http://ubuntuforums.org/showthread.php?t=1411495](http://ubuntuforums.org/showthread.php?t=1411495)
You mean ntdetect and ntldr can't be on a logical partition, that is right. Yes the boot is via sda1. sda1 is there only for that purpose.
But it still needs a primary to boot from.
[http://www.sousuke.org/wiki/Installing_Windows_on_a_logical_partition](http://www.sousuke.org/wiki/Installing_Windows_on_a_logical_partition)
[http://support.microsoft.com/kb/306559#f1](http://support.microsoft.com/kb/306559#f1)

---

### Post by Robert Elkow on 2010-03-31
In my thread entitled Quadruple booting a MacPro I can use rEFIt to boot into three operating systems, Snow Leopard, Windows 7 - 64, and Windows xp service pack 3.  Installing Ubuntu AMD64, depending on how I designate where GRUB is to be  located may or may not make a difference.  If I use the pull down to the right and indicate sda5 everything works as before and I can boot using rEFIt into three operating systems, Snow Leopard, Window 7, and xp.  Not Ubuntu.  If I write (hd0,4) in the box for where to put GRUB, I can only boot Snow Leopard, Windows 7, and Ubuntu, not xp.  Snow Leopard, and Windows 7 are available as before through rEFIt.  The rEFIt icon for partition 4 is now a legacy partition and contains GRUB from which I am supposed to be able to boot all four operating systems but the xp in partition 4 gives me GRUB again.  Also the icon which appeared before in rEFIt for HD legacy is missing.

---

