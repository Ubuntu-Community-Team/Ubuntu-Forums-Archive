---
title: "GRUB was unable to install to hd3"
date: 2006-11-07
forum: Installation &amp; Upgrades
---

### Post by Bartender on 2006-11-07
Ubuntu on 1st partition (hda1), PCLOS on 2nd (hda3).  I asked PCLOS to install GRUB in its own partition.  Edited Ubuntu GRUB "menu.list" so that PCLOS chainloads.  That part works.  

Today I tried to install Kubuntu 6.10 to a 3rd partition, hda4.  Right at the end I got a "fatal error GRUB unable to install to hd3". I closed out and rebooted into Ubuntu.  Looked at hda4.  It appears Kubuntu installed.  
The Kubuntu GRUB looks basically identical to [herman's]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") picture (figure 6) but I have "default" instead of "menu.lst".  Is it worth it to try and fix GRUB or should I try reinstalling entirely?  I'm not sure asking GRUB to install to hd3 was right but putting GRUB inside the "/" partition was how I did PCLOS...

---

### Post by taurus on 2006-11-07
From a terminal, what is the output of this command?

```
sudo fdisk -l
```

---

### Post by confused57 on 2006-11-07
Maybe you could reinstall grub to the Kubuntu partition using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

If Kubuntu is on partition 4, you'd specify **root (hd0,3)**, then
**setup (hd0,3)**

You might want to check the output of the command taurus suggested, to make sure Kubuntu is on partition 4.

hd3 would be hard drive #4, not partition #4

---

### Post by Bartender on 2006-11-08
Hey, guys, thanks very much for the replies.  

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        5112    41062108+  83  Linux
/dev/hda2           14359       14593     1887637+   5  Extended
/dev/hda3            5113        9753    37278832+  83  Linux
/dev/hda4            9754       14358    36989662+  83  Linux
/dev/hda5           14359       14593     1887606   82  Linux swap / Solaris

I gotta sneakernet any data from the Linux PC to the Windows PC...

Looks like confused57 identified my screwup.  I shoulda typed in hd0,3 instead of hd3 when Kubuntu asked where to put GRUB.  I'll re-install and try again.  I need the practice :rolleyes:

EDIT: Whoohoo it worked.  Added

title           Ubuntu
rootnoverify    (hd0,3)
chainloader +1

to the GRUB menu.lst in the original Ubuntu install, rebooted, and now can scroll thru original Ubuntu, PCLOS, or Kubuntu when PC first starts up.  I could probly go back and edit the "title" line to Kubuntu but might leave well enuf alone...

---

