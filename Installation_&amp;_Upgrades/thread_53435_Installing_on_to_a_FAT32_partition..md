---
title: "Installing on to a FAT32 partition."
date: 2005-07-31
forum: Installation &amp; Upgrades
---

### Post by c0rrupt on 2005-07-31
I noticed that in Ubuntu Setup it is possible to format a partition as FAT32.  Is it also possible to install Ubuntu on a FAT32 partition?

---

### Post by bored2k on 2005-07-31
[QUOTE=c0rrupt]I noticed that in Ubuntu Setup it is possible to format a partition as FAT32.  Is it also possible to install Ubuntu on a FAT32 partition?[/QUOTE]
 Yes it is possible to format to FAT32. Yes you can install to a FAT32, but the question is: why would you want to ? Linux native partitions like reiserFS and EXT3 are far, far better.

---

### Post by c0rrupt on 2005-07-31
Well, If I ever boot into Windows I want to be able to copy files from my Linux partition if I need to.  I was going to use ReiserFS.  Do you know of a good program to let me do that in Windows?

---

### Post by bored2k on 2005-07-31
[QUOTE=c0rrupt]Well, If I ever boot into Windows I want to be able to copy files from my Linux partition if I need to.  I was going to use ReiserFS.  Do you know of a good program to let me do that in Windows?[/QUOTE]
 If you want to boot into Windows and be able to copy files (just copy) use EXT3). With Explore2Fs you can view and copy files should you want to. In my case, I've been using ReiserFS and If I ever need files, I just copy them from Linux to Windows.

[http://ubuntuguide.org/#readlinuxpartitionsinwindows](http://ubuntuguide.org/#readlinuxpartitionsinwindows)

---

