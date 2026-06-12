---
title: "Where do I install GRUB?"
date: 2007-02-17
forum: Installation &amp; Upgrades
---

### Post by Sicilianmandolin on 2007-02-17
I'm dual booting Windows XP and Ubuntu and I need to know where to install GRUB. Here's the "Ready to install" log that's been generated: (note where GRUB is to be installed)

 Language: English
 Keyboard layout: U.S. English
 Name: Giuseppe Listro
 Login name: sicilianmandolin
 Location: America/Los_Angeles
 GRUB will be installed to (hd0)


If you continue, the changes listed below will be written to the disks.
Otherwise, you will be able to make further changes manually.

WARNING: This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted.

The following partitions are going to be formatted:
 partition #5 of SCSI1 (0,0,0) (sda) as ext3
 partition #6 of SCSI1 (0,0,0) (sda) as ext3
 partition #7 of SCSI1 (0,0,0) (sda) as swap

(Oh, and you'll notice only the 3 partitions selected for Ubuntu because I unselected my Windows XP and Recovery partitions. But then I noticed it says "This will destroy all data on any partitions you have removed..." so, by unselecting my other 2 partitions, will it delete them???)

---

### Post by solar george on 2007-02-17
That ought to work - GRUB will overwrite the XP boot loader but the menu will include an option to boot into XP

---

### Post by Sicilianmandolin on 2007-02-17
> **solar george said:**
> That ought to work - GRUB will overwrite the XP boot loader but the menu will include an option to boot into XP

Alright, cool. Thanks... but: you'll notice only the 3 partitions selected for Ubuntu because I unselected my Windows XP and Recovery partitions. But then I noticed it says "This will destroy all data on any partitions you have removed..." so, by unselecting my other 2 partitions, will it delete them??? :|

---

### Post by solar george on 2007-02-17
> by unselecting my other 2 partitions, will it delete them???
I think that what it means by removed 
> This will destroy all data on any partitions you have removed
is ones that you have deleted using the partitioner - So no.

But I always use the textmode installer so I might be wrong.

---

### Post by Sicilianmandolin on 2007-02-17
Alright, I'll take your word for it! *crosses fingers*

Thanks.

---

### Post by solar george on 2007-02-17
Good Luck

---

