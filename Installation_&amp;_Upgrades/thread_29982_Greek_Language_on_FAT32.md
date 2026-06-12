---
title: "Greek Language on FAT32"
date: 2005-04-26
forum: Installation &amp; Upgrades
---

### Post by Fireball on 2005-04-26
I just finished the installation of Hoary. I decided to create a FAT32 partition since I have a dual boot system. The problem goes as following:

I fave a portable hard drive NTFS formatted. I am able to see all the files and folders even those with greek names.

On the contrary when I copied the contents of the portable HDD to the FAT32 partition I can only see the english named folders but not the greek. Instead, for every greek file or folder there are question marks and not greek characters.

What Should I do?

---

### Post by gugus on 2005-04-27
I had the same problem with my French FAT32 partition,

Here the line in my /etc/fstab with solve my problem:
/dev/hda1 /mnt/windows vfat umask=000,,utf8,codepage=850 0 0

---

