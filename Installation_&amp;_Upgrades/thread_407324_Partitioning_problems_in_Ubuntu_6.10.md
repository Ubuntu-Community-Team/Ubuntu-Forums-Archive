---
title: "Partitioning problems in Ubuntu 6.10"
date: 2007-04-12
forum: Installation &amp; Upgrades
---

### Post by roxtar on 2007-04-12
Hi,
I was trying to install Ubuntu 6.10 x86_64 on my machine. As the installation was going on really slow (effectively I have only 192 MB of RAM)  I decided to give it some swap space which I had from an earlier Linux installation. When the partition manager showed up I decided to partition manually. My partition tables looks something like this:

/dev/hda1 FAT32
/dev/hda2 Extended
/dev/hda5 NTFS
/dev/hda6 NTFS
/dev/hda7 reiserfs
/dev/hda8 swap


I had done a "swapon /dev/hda8" before the installation began. 
Now, I selected to mount /dev/hda7 on /, /dev/hda8 on swap. But, when I click on "Forward", I get an error message saying that "No root partition selected". I couldn't do a "swapoff /dev/hda8" because the total memory usage was somewhere around 230 MB (67% in RAM and 33% in swap space). 
Any ideas how to get around this? (except, of course, buy more memory)

---

### Post by roxtar on 2007-04-12
I think this is a bug in the installation wizard. You can't mount an existing partition as root ('/') and ask the installation wizard to format it. The way I got around the problem was by deleting my /dev/hda7 partition and creating a new one from the space freed.

---

