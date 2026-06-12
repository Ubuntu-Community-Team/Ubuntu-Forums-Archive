---
title: "Installation Woes (Disk Setup)"
date: 2005-03-11
forum: Installation &amp; Upgrades
---

### Post by curator on 2005-03-11
When doing disk partitioning/setup, I can set up partitions fine, but when I move on to where it formats (regardless of filesystem), the background turns red and it claims 'failed to create file system'.  Partition 1 is NTFS and I'd prefer to leave it alone.  2 is swap and 3 is ext3.  (I've tried doing it in the other order and will all the other fs choices.)  Hitting alt-f3, I see error messages from mke2fs and tune2fs relating to a missing /dev/ide/host0/bus0/target0/lun0/part3.  part3 and part2 are in fact both missing, only part1 is present.  /proc/partitions lists only the first partition.  However, both the installer and cfdisk list all three partitions.  Any idea what the issue might be?

This thread appears to describe a similar issue, left unresolved:
[http://www.ubuntuforums.org/showthread.php?t=3623](http://www.ubuntuforums.org/showthread.php?t=3623)

The LiveCD works fine and I've had a gentoo install previously that worked okay.  After seeing the LiveCD, I'm excited about making this work, however this has me completely stuck.

For what it's worth, I have an nforce2 board and dmesg shows the nforce2 ide controller.

Help!

Thank you.

---

### Post by curator on 2005-03-11
Another note, I've tried formatting from the livecd and then using the preformatted partition during installation.  It also fails, similarly reporting a missing .../part2.

Thanks again.

---

### Post by bored2k on 2005-03-11
[QUOTE=curator]Another note, I've tried formatting from the livecd and then using the preformatted partition during installation.  It also fails, similarly reporting a missing .../part2.

Thanks again.[/QUOTE]
 Did you validate the disc for correct download (md5sum). If not, grab a checksum verifier (google is your friend) and get one for whatever OS you're running at the moment. In that app., check the downloaded .iso, it will give you a value, it must match the value given in the website you downloaded ubuntu from (in the section md5sums).

You can also try installing "leaving partition as it is" if you can manage to format the partition with another application and retry. Not recommended though, as your disk is probably corrupt and installation will go wrong.

---

### Post by curator on 2005-03-11
MD5 sum checks out.  I tried the leaving partition as is after creating it with the livecd.  It generates errors when it fails to mount it (relating, I think to the missing part3 in /dev/ide...).

Is there any way to fix or work around this?

---

### Post by curator on 2005-03-11
Installed using Hoary instead of Warty, problem went away.

Thanks for the help.

I'm very impressed with how professional this distribution is!

---

