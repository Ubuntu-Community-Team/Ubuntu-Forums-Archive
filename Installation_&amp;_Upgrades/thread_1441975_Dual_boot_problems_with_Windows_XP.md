---
title: "Dual boot problems with Windows XP"
date: 2010-03-29
forum: Installation &amp; Upgrades
---

### Post by vince_dc on 2010-03-29
Hi, 

I had some problerms during the installation of ubuntu 9.10 (bad CD) which nuked Window, what was installed on another partition. I finally managed to install ubuntu, but he doesn't see my windows partition ... 

I found the partition and mounted it. 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       20919   168023835    f  W95 Ext'd (LBA)
/dev/sda2   *       20920       60801   320352165   83  Linux
/dev/sda5               2       20168   161991396    7  HPFS/NTFS
/dev/sda6           20169       20919     6032376   82  Linux swap / Solaris

But ntldr, ntdetect.com and boot.ini where missing.

I copied both ntldr and ntdetect.com from an installation cd and recreated the boot.ini file. (not sure that is right) 

I added the following to the /boot/grub/grub.cfg : 
menuentry "Windows XP" {
set root=(hd0,5)
chainloader +1
}

But I still get an error trying to boot XP: 
A disc error occured.

What am I doing wrong ? :-)

---

### Post by coffeecat on 2010-03-29
Somehow, you've managed to get your Windows C: partition onto a logical partition (sda5). Windows can't boot from a logical partition. It either needs to be in a primary partition itself, or have its boot files on a primary partition. This is a bit dated, but have a look at this link:

[http://www.sousuke.org/wiki/Installing_Windows_on_a_logical_partition](http://www.sousuke.org/wiki/Installing_Windows_on_a_logical_partition)

It probably explains it a bit better than I can.

Out of interest: how did Windows get to be on sda5? Was that some sort of manufacturer's quirk? Was there a primary boot partition before you tried to install Ubuntu the first time?

---

### Post by vince_dc on 2010-03-29
It was a pre-installed crap that I got before ... But I re-installed it. 
Never thought of that before ...

---

### Post by vince_dc on 2010-04-02
ok ... but now how to recover that partition ? 
don't have a clue ...

---

### Post by coffeecat on 2010-04-02
> **vince_dc said:**
> 
don't have a clue ...

Me neither - I've only ever had Windows C:\ on a primary. However, this may or may not help. I found it in my bookmarks.

[http://www.zyxware.com/articles/2008/07/20/how-to-install-and-boot-windows-on-a-logical-parition](http://www.zyxware.com/articles/2008/07/20/how-to-install-and-boot-windows-on-a-logical-parition)

---

