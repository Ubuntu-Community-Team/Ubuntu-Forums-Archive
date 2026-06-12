---
title: "Mount Point"
date: 2009-12-18
forum: Installation &amp; Upgrades
---

### Post by gameguy on 2009-12-18
I am having some problems with file systems.
I have three partitions: Linux (ext3), Data (FAT32), Windows 7(NTFS).
I have acronis disk director and trueimage, so I can backup, change file system type, then restore.
Is there a file system type I can use for my Data drive that both Windows and Linux can both read and write.
Also, I would need to change the mount point of my home folder in both Windows and Linux, so if anyone knows how to do that (but not so important in windows since my dad knows how, but I don't see him for a while.
At the moment I have to boot into windows and copy the file I want to access on my documents folder, then since I don't want to reboot each time, I usually end up doing whatever on Windows anyway (the horror)

Necesary:
Windows-see Data, done.
Linux-see Windows, done, and Data=/home, not done.

Unnecasary but useful:
Windows-See Linux (without using ext2fs)

I've done a backup for a start. I tried using mount manager and it works fine until you reboot, where it comes up with something about /home/matt/.IECauthority and /usr/???. It then boots up but doesn't load the desktop.

---

### Post by CharlesA on 2009-12-18
Isn't linux able to write to NTFS?

If you need to pick a file system, I'd go with ext3/4, you could always run ext2fs on Windows so that it'll see the data partition.

---

### Post by garvinrick4 on 2009-12-18
Set up a Windows network in 7 and samba in linux and while in linux your
C: drive will show up in Places on Linux and your Linux will show up in 7 on Windows
network. You can then swap files or if you have a USB drive for backup you can see
all devices on the network also. Eventually you only go to Windows to update.
I am sure you already know what files each will open and what you can swap.

---

### Post by bkmfs on 2009-12-18
to permanently mount files you will have to edit /etc/fstab.  Here is a link:

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Also you should be able to get into you ntfs file system without any problems.  You just have to mount it first.  A quick temporary way might be to go 'places->computer->' and click on the media drive that your windows is on.  Also, remember that on the fat32 file system you cannot store files larger than 4GB.  You might as well replace that with another ntfs file system.

---

### Post by gameguy on 2009-12-19
Windows is now set up on fat32 data drive so nothing needed there.

---

