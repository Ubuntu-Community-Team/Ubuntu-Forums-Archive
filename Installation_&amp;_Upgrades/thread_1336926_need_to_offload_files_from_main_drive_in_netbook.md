---
title: "need to offload files from main drive in netbook"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by cheshirekow on 2009-11-25
Sorry for the long narrative.

I have an asus eee pc 901. It has two solid state drives. One 4GB and one 15GB for a total of 20GB. So I previously had xp on this machine. I installed the ubuntu netbook remix on the 4GB partition. I want to use this machine for some development so I installed the following:

thunderbird
filezilla
gparted
eclipse (w/ CDT, texlipse, EPIC)
build-essentials
git-core
sun-java6-jre
gcc-avr
avr-libc

After that, I was completely out of space on that partition. I used gparted to format the 15GB partition and mounted it as my /home directory. However, I've still only got a couple 100MB left on the main drive. 

The reason for using the 4GB drive for the main file system is it's alot faster. And I mean ALOT. So, my question is, what is the best way to distribute the file system over these two drives. One small and fast, one big and slow. 

I've only been using linux for a little while. I'm pretty good around the basic system commands but I don't really know that much about the inner workings, or something more advanced like dealing with multiple drives. For instance, I've learned how to mount the second drive as the /home directory, but I have no clue how I would mount the drive as multiple directories. Any help regarding tools to use to do this, and recommendations on what I can offload on that second drive so as to minimize performance degradation would be greatly appreciated.

Thanks in advance.

---

