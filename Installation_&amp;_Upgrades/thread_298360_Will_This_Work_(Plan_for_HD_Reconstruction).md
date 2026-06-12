---
title: "Will This Work? (Plan for HD Reconstruction)"
date: 2006-11-12
forum: Installation &amp; Upgrades
---

### Post by Virtute on 2006-11-12
After a few weeks of not having any idea of what to do, I have come up with a plan for dual booting - I don't have anywhere to back up data to, though, so if someone could give me a thumbs up I'd appreciate it.

The Situation:
Have a 200gb Ubuntu installation taking up every last meg of a 200gb HD.  Want to dual boot to Windows.

Plan:
1. Use bootable partition manager to resize Ubuntu down to 100gigs.
2. Use same partition manager to format remaining 100gigs with FAT32.
3. Boot into Ubuntu, mount the newly created partition, and drag the files I want to backup onto the partition.
4. Install Windows to the partition.
5. From there I can easily fix my boot loader knowing that my files are safe on a partition that I can easily boot to.  The reason for all this is that I know when you install windows, it automatically rewrites your MBR to the windows partition, and I didn't want to get into a situation where all my files were on the Ubuntu partition, which I wouldnt be able to access due to Windows having owned my bootloader.

---

### Post by tszanon on 2006-11-12
It seems to work, if I got it:
1. Resize partition P1;
2. Create new partition P2 (FAT32)
3. Copy/move important files from P1 to P2;
4. Install Windoze in partition P1. It will rewrite MBR;
5. Move important files from P2 to P1;
6. Install Ubuntu in partition P2.

If what you are going to do is what I've written above, I believe it will work. Never done this before, but that is what I would do in this situation.

Good luck!

---

### Post by gn2 on 2006-11-13
I would buy a second hard drive: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

Much easier :)

---

### Post by gnomeza on 2006-11-13
Beware that if you're backing up from a Linux filesystem to a FAT32 filesystem you're likely to lose metadata (file permissions, owner, etc) and possibly cause filename collisions (when translated, two filenames end up the same - there are some characters that FAT32 just doesn't handle well).
It's also possible to hit FAT32 filesystem limits like the maximum number of files in a directory and maximum path length.

So.
Use the tar utility to backup safely to an archive:
```
tar -cvf /my/fat32/partition/my-backup-archive.tar /my/files/for/backup
```

But there's a further problem. FAT32 has a filesize limit of 4GB. So you may have to create a bunch of archives < 4GB each.

So take careful note of these limits: [http://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits](http://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits).

In truth, you're possibly better off installing an ext2/3 driver for windows (they're out there, I promise).

---

### Post by cotcot on 2006-11-13
This seems more a situation to install XP as virtual drive with VMWare server.
I recently tried it on an usb hhd using this howto [http://ubuntuforums.org/showthread.php?t=183209]("http://ubuntuforums.org/showthread.php?t=183209")and that worked perfect.

---

