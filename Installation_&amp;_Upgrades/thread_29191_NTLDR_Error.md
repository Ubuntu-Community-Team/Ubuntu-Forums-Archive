---
title: "NTLDR Error"
date: 2005-04-23
forum: Installation &amp; Upgrades
---

### Post by leezer3 on 2005-04-23
Just installed Ubuntu over an older Mandrake install, by formatting the partition. Windoze XP is installed on 1st partition (FAT 32), & is recognised in Grub. Linux is on the 2nd EXT3 partition. However, XP will not boot, tells me that NTLDR is missing :(
Notes:
Mandrake had Lilo installed, booted fine.
Only told installer to format Linux partition, & set bootable flags on Windows & Linux, no more.

Final point, I can't find how to map the Windows partitions in Linux.

Help!

-Leezer-

---

### Post by localzuk on 2005-04-23
First I'll look at point 2, to do this you need to know the partition number. Assuming it is /dev/hda0, you should create a dir in /media called /media/hda0 (sudo mkdir /media/hda0)

Now, try running:

mount -t vfat /dev/hda0 /media/had0

This should mount it to the directory.

If you want it to mount automatically on start up, alter your /etc/fstab to include a line like:

/dev/hda0 /media/hda0 vfat defaults 1 1

Now, once you have this done you can check on the partition to see if 2 filse ('ntldr' and 'ntldr.com' still exists (in the partitions root directory). If it doesn't, boot from your windows xp cd, and load repair mode. Now copy the files from your cd (d:\i386\ntldr and d:\i386\ntldr.com) to your c:\ drive.
(Instructions at: [http://www.computerhope.com/issues/ch000465.htm](http://www.computerhope.com/issues/ch000465.htm))

---

### Post by leezer3 on 2005-04-25
[QUOTE=localzuk]First I'll look at point 2, to do this you need to know the partition number. Assuming it is /dev/hda0, you should create a dir in /media called /media/hda0 (sudo mkdir /media/hda0)

Now, try running:

mount -t vfat /dev/hda0 /media/had0

This should mount it to the directory.

If you want it to mount automatically on start up, alter your /etc/fstab to include a line like:

/dev/hda0 /media/hda0 vfat defaults 1 1

Now, once you have this done you can check on the partition to see if 2 filse ('ntldr' and 'ntldr.com' still exists (in the partitions root directory). If it doesn't, boot from your windows xp cd, and load repair mode. Now copy the files from your cd (d:\i386\ntldr and d:\i386\ntldr.com) to your c:\ drive.
(Instructions at: [http://www.computerhope.com/issues/ch000465.htm](http://www.computerhope.com/issues/ch000465.htm))[/QUOTE]


NTLDR was already there, as was NTDetect.com . I suspect that setting the bootable flag on the Windoze drive was not a good idea. Anyway, formatted, & all  is working perfectly with the disks. :D
Now I have to figure out IPW2100 & MP3's!

Thanks!

-LeEzEr-

---

