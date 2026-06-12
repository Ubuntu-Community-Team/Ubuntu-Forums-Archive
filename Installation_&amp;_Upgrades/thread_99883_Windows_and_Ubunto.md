---
title: "Windows and Ubunto"
date: 2005-12-06
forum: Installation &amp; Upgrades
---

### Post by justanothor on 2005-12-06
Okay I have windows xp on one hd and ubunto on the other. When I run either os they dont recognize the other drive even though both are connected to the motherboard. How do I fix this problem? 

I hope I posted this in the right section....I'm new so any help would be appreciated.

---

### Post by aysiu on 2005-12-06
Windows won't recognize Ubuntu.

Ubuntu *can* recognize Windows with a little help, though:
[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

---

### Post by towsonu2003 on 2005-12-06
take a look at this (windows seeing ubuntu's drive), but use it with caution. [http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)

---

### Post by Joe_CoT on 2005-12-06
the problem comes down to this:
Windows can't recognize ext (linux) filesystems. there are programs like explore2fs, but they're read-only, and using one that claims it can read and write is a good way to hose the partition.

Linux can read ntfs drives, but it can't write to them reliably. You should always set mounted ntfs drives to read only.

The only real compromise that i've found is that both read and write fat32 drives just fine. It's not the most efficient filesystem in the world, and it's max file size is 4GB (ie doesn't work for dvd images), but it gets the job done. you'd want to make the partition in windows, restart into ubuntu, and use the console program mkdosfs (in the dosfstools package) to format the drive.
the command would be:
sudo mkdosfs -F 32 -volname /dev/hda1

where "volname" is what you want to name the partition, and "/dev/hda1" is the location of the partition you want to use. you may want to use fdisk to figure out the partition number.

---

