---
title: "XP + Ubuntu on 1TB RAID-0 Possible ?"
date: 2011-03-20
forum: Installation &amp; Upgrades
---

### Post by dredogol on 2011-03-20
(This is for a 100% Clean install)

**[COLOR=Red]Q1)[/COLOR] ** **I was wondering if it is possible to Dual boot Ubuntu with Windows XP on a 1TB RAID-0 setup ?**

**[COLOR=Red]Q2)[/COLOR] ** **Also, is it possible to create a SWAP partition (for Ubuntu) on a NON RAID-0 HDD ?**

**[COLOR=Red]Q3)[/COLOR] ** **Lastly... I read GRUB2 is the default boot manager... should I use that, or GRUB / Lio ?**

I have a total of 3 HDDs on this system:
-- 2x 500GB WDD HDDs (non-advanced format) ... RAID-0 setup
-- 1x 320GB WDD HDD (non RAID setup)
(The non RAID HDD is intended to be a SWAP drive for both XP and Ubuntu = 2 partitions)

I plan on making multiple partitions... and reserve partition space for Ubuntu (of course).

I have the latest version of the LiveCD created already.
**[COLOR=Red]Q4) [/COLOR]Do I need the Alternate CD for this setup?**

I plan on installing XP before Ubuntu.

This is my 1st time dual booting XP with Ubuntu.

I'm using these as my resources:
-- [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
-- [http://www.youtube.com/watch?v=-x2rZe2Z9as](http://www.youtube.com/watch?v=-x2rZe2Z9as)
[COLOR=Red]
[/COLOR]**[COLOR=Red]Q5)[/COLOR] Anything else I should be aware of (possible issues during install)?**

**[COLOR=Red]Q6) [/COLOR]Lastly... is there anything like the AHCI (advanced host controller interface) like in Windows for Ubuntu?**
(Since I need a special floppy during Windows Install...)
I want to be able to use the Advanced Queuing capabilities of my SATA drives in Ubuntu.

Thanks.

---

### Post by TexasRussian on 2011-03-20
Yes, this is very possible.  using Gparted this will be a breeze.
As I understand it you currently have installed Windows XP. After installing ubuntu on it's separate partition it will automatically detect Windows XP and will set up GRUB2. If for some reason Grub doesn't work, you can install EasyBCD on your Windows XP partition, this will allow you to create your own Grub like menu for start up OS selection.

The answer to your second question is yes, as long as you have that partition created and set as a SWAP partition before you install ubuntu on it's partition, ubuntu will automatically use it.

Answer to question three is, no. As long as you have the current CD burnt correctly from the ISO it should work fine.awd

And lastly, I don't know much about AHCI so I'll leave that answer to someone else. lol
Hope I helped!****

---

### Post by dredogol on 2011-03-20
> **TexasRussian said:**
> Yes, this is very possible.  using Gparted this will be a breeze. As I understand it you currently have installed Windows XP. After installing ubuntu on it's separate partition it will automatically detect Windows XP and will set up GRUB2. If for some reason Grub doesn't work, you can install EasyBCD on your Windows XP partition, this will allow you to create your own Grub like menu for start up OS selection.
 The answer to your second question is yes, as long as you have that partition created and set as a SWAP partition before you install ubuntu on it's partition, ubuntu will automatically use it.
 Answer to question three is, no. As long as you have the current CD burnt correctly from the ISO it should work fine.awd
Thanks for the answers.

Does anyone have answers to Qs 4, 5, or 6?

---

### Post by dredogol on 2011-03-23
Still no answers to my other Questions?

---

### Post by Hedgehog1 on 2011-03-23
> **dredogol said:**
> 
**[COLOR=Red]Q1)[/COLOR] ** **I was wondering if it is possible to Dual boot Ubuntu with Windows XP on a 1TB RAID-0 setup ?** 1) True Hardware Raid (No drivers): Yes
2) 'FakeRaid': Yes
3) Software Raid: NO, must be RAID1 for Ubuntu boot
> **[COLOR=Red]Q2)[/COLOR] ** **Also, is it possible to create a SWAP partition (for Ubuntu) on a NON RAID-0 HDD ?**Yes, a Linux-Swap partition on a separate disk is fine - but it must Non-Raid or Software RAID 1 or True Hardware Raid
> **[COLOR=Red]Q3)[/COLOR] ** **Lastly... I read GRUB2 is the default boot manager... should I use that, or GRUB / Lio ?**
Start with Grub.  Works fine.  You can try another if you are unhappy with it.> **[COLOR=Red]Q4) [/COLOR]Do I need the Alternate CD for this setup?**Nor for real hardware RAID, no.  FakeRaid & Software RAID, I am not sure
> [/COLOR]**[COLOR=Red]Q5)[/COLOR] Anything else I should be aware of (possible issues during install)?**In partical terms, plan to install your setup twice.  Once to find out things things you didn't know to ask, the second time for real.
> **[COLOR=Red]Q6) [/COLOR]Lastly... is there anything like the AHCI (advanced host controller interface) like in Windows for Ubuntu?**
(Since I need a special floppy during Windows Install...)
I want to be able to use the Advanced Queuing capabilities of my SATA drives in Ubuntu.Floppy drives are still supported in Ubuntu. 

AHCI is supported out of the box on Linux operating systems (from kernel 2.6.19 onwards).

***The Hedge***

:KS

---

