---
title: "WinXP won't boot after Ubuntu installation"
date: 2005-03-17
forum: Installation &amp; Upgrades
---

### Post by jbeaudet on 2005-03-17
Hi everyone,

I installed yesterday Ubuntu (Hoary) on my thinkpad T41 with winXP preinstalled.  I wished to keep this XP installation so I opted for a dual boot.

(Previously, I ordered install CD's from IBM so I could sweep the pre-install partition)

As I installed Ubuntu, I could see 4 partitions on my 40GB HD. 
-
/dev/hda1  (C:)  ntfs   12GB
/dev/hda2 (D:)   fat32   16GB
/dev/hda?          free     4,3 GB
/dev/hda?          free     ? GB

During installation, I choosed to delete the last 2 partitions and to use this space for linux.  It used this space to create 2 partitions, / and swap. Everything went well and I rebooted choosing Ubuntu in Grub.  Ubuntu worked just fine.  

However, this morning, I attempted to reboot in WinXP and I had an error message. 

[COLOR=Red]A problem has been detected ......

UNMOUNTABLE_BOOT_VOLUME

Check to make sure any new hardware or software is properly installed
[/COLOR]


In Ubuntu, I couldn't see my windows partitions so I booted with Knoppix (3.7) and used QTParted to see my partitions.

Now, I have 8 partitions... 

[FONT=Courier New]
**01  /dev/hda-1   free     0.03MB**
02  /dev/hda1    ntfs      12GB
03  /dev/hda2    fat32     16GB
**04  /dev/hda-1   free       3.69MB**
05  /dev/hda3    ext3       8.84GB
06  /dev/hda4    extended   423,39 MB
    **07  /dev/hda-1   free     0.03MB**
    08  /dev/hda5    linux-swap   423MB
[/FONT]

I suspect that I can't boot winXP because of the /dev/hda-1 that precedes the /dev/hda1. 

Any ideas?

Regards,

--
Jean

---

### Post by macewan on 2005-03-17
This doesn't apply to the question but you may want to edit this post and select **Disable smilies in text** under  Additional Options > Miscellaneous Options

---

### Post by jbeaudet on 2005-03-17
Done. Thanks!

---

