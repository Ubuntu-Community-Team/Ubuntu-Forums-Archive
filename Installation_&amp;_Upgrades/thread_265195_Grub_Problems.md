---
title: "Grub Problems"
date: 2006-09-25
forum: Installation &amp; Upgrades
---

### Post by geezerone on 2006-09-25
Hi

Just installed dapper onto a single SATAII hard drive which has a windows XP NTFS partition, then extended partition containing NTFS (data) and /home (ext3). I also have a swap and / (both primary ext3) which have (or so I believe) Ubuntu installed.

The problem is, that upon booting only XP option is shown. I checked to see where Grub thinks Ubuntu is installed (from terminal) and says (hd2,3) ex2fs partition x83  - I then installed Grub here and grub menu displayed but wouldn't load Ubuntu (says wasn't there i think) and the windows bootloader got corrupted. I repaired using the XP console but now back to just XP loading.

Any ideas appreciated. :-k

---

### Post by hajk on 2006-09-25
I'm not really sure what your hardware and partitions layout is...
You mention (hd2,3), which would be the fourth partition on the third disk, is that right? Being SATA2, that would be equivalent to /dev/sdc4. 

From what disk is XP loaded, /dev/sda perhaps? And where is Grub installed -- also on /dev/sda? 

We really need more info on this, like the full partition tables on the drives involved.

---

### Post by geezerone on 2006-09-26
Just thought I would post an update.

I had a brainstorm ;) and decided to remove all disks apart from my SATAII drive and installed over the existing partitions (dev/sda 3 [swap],4 [/ ] and logical 6 [/home]. After rebooting Grub 1.5 loads and so do the options to choose between XP and Ubuntu. I booted into both OS's successfully and amended the 'menu.lst' file in grub to set default as XP and changed timeout to 3 secs.

I suspect that grub was writing to my master IDE drive mbr record but this way there was no way it could write to any disk as only one there!

So thanks for the answer. :)

---

