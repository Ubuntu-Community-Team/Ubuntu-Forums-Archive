---
title: "questions about partitions"
date: 2005-04-11
forum: Installation &amp; Upgrades
---

### Post by ultima2k on 2005-04-11
I'm gonna install ubuntu together with Windows(dualboot).
Now I got a big question..

I have two drives with 320GB of file-storage as a NTFS-partition, windows-standard blabla....

Now that I'm gonna use ubuntu-linux I've seen that you can't write to NTFS-partitions or you can screw it up.

So, if they are NTFS you can use 'em in windows, but not in linux, and if you use linux's file-systems it won't work in winhoes...


Solution anyone??

---

### Post by Buffalo Soldier on 2005-04-11
My "solution" is not for everyone. When I installed M$ Windows earlier, I've format the partition as FAT32 (VFAT). Another way is to create a "middle ground".

Partition 1 - NTFS - M$ Windows
Partition 2 - VFAT - shared area
Partition 3 - EXT3 - Linux
Partition 4 - swap

And there are a few apps that you can install in windows to browse linux partition. But I forgot the name. Anyone?

---

### Post by ultima2k on 2005-04-11
Ok, I really wonder why it doesn't work good writing to NTFS-partitions with linux, it would solve my problem :S
I mean, there's no problem reading from them, but ofcourse I wanna be able to write too..

Well I could format them as Fat32, but I have heard that it would be slower than with NTFS..

---

### Post by ChrisTheGeek on 2005-04-11
Since you'll be dual booting you may want to check out:

[http://www.jankratochvil.net/project/captive](http://www.jankratochvil.net/project/captive)

It uses the native NT kernel files to provide safe read/write NTFS access.

---

### Post by ultima2k on 2005-04-12
So with that I can use my NTFS-partitions with linux (read/write)?

---

### Post by ChrisTheGeek on 2005-04-12
I haven't used it myself (since I'm not dual booting) but my understanding is that it uses WINE and a copy of certain NTKernel files to allow full read/write.  It's 'safe' since it's using the actual Windows kernel to write to the disk not a reverse engineered program. Have a google for Captive NTFS and read the project pages for more info.  

If this doesn't seem right for you then I would recommend a FAT32 shared partition since, afaik, this is the only file system both Windows and Linux understand.  FAT32 is definately inferior to NTFS since it's slower and more importantly not a journaled file system.  Journaled systems are better since they keep a separate track of the changes in a log in addition to the main indexes.  Without boring you with techy stuff, this makes the file system much harder to corrupt and more resiliant.  Nonetheless, FAT32 will probably work fine for you until you can ditch Windows for good :)

---

