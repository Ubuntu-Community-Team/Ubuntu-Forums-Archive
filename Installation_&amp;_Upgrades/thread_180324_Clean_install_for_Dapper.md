---
title: "Clean install for Dapper"
date: 2006-05-22
forum: Installation &amp; Upgrades
---

### Post by graabein on 2006-05-22
Hi, 

I have been running the same installation of Ubuntu since I first partitioned my Windows box and added Hoary. I upgraded to Breezy with minor problems. Now that Dapper is right around the corner I think I want to do a clean install.

I have / (root?) and /home on separate patitions. How do I do a clean install when I have downloaded (bittorrent) and burned Dapper to CD?

Here is my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /home           ext3    defaults        0       2
/dev/hdd        /media/dvd   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy  auto    rw,user,noauto  0       0
/dev/sda1	/mnt/store	ext3	defaults	0	2
```

---

### Post by NoUse on 2006-05-22
I assume you want to keep the files in your home partition.  All you need to do is boot off the CD and run the manual partitioner in the installer.

Tell it to format /dev/hda5 and use it for root and tell it to use (not format) /dev/hda6 for /home.

That should install all new system software and retain your home directory.

I don't see a swap partition.  Do you have one?

---

### Post by Sef on 2006-05-22
**Back up** your data first.  On occassion, your home partition can become corrupted and your data lost.

If you have  1 GB or more of ram, you don't need a swap partition, unless you are into video editing or other memory intensive memory applications.

---

### Post by az on 2006-05-22
[QUOTE=graabein]Hi, 

I have been running the same installation of Ubuntu since I first partitioned my Windows box and added Hoary. I upgraded to Breezy with minor problems. Now that Dapper is right around the corner I think I want to do a clean install.
[/QUOTE]

Dist-upgrade and then do a clean install if it not completely elegant and you don<t want to spend any time figuring what you need to do.  It will most probably work, though, if you wait until release.  The last bits they usually fix are the dist-upgrade tweaks.

---

### Post by graabein on 2006-05-24
[QUOTE=azz]Dist-upgrade and then do a clean install if it not completely elegant and you don<t want to spend any time figuring what you need to do.  It will most probably work, though, if you wait until release.  The last bits they usually fix are the dist-upgrade tweaks.[/QUOTE]

Thanks for the answers!

What are the pro's for doing this azz? I plan on downloading dapper through bittorrent and doing a clean install sometime in the first week of June...

And no, I don't have swap memory... I have 1 GB ram and just do regular stuff in GNU/Linux (and play games on dual booting XP).

---

