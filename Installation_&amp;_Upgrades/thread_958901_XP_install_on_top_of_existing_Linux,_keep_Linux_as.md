---
title: "XP install on top of existing Linux, keep Linux as main"
date: 2008-10-25
forum: Installation &amp; Upgrades
---

### Post by TheOneFreeman on 2008-10-25
I have just converted to Ubuntu from Windows XP after a series of annoying crashes. But, since I am a gamer, along with the fact that Wine is still pretty touch and go with some games AND Fallout 3 is coming out, I am forced to conclude that I might need XP again. 

Currently, I have 2 hard drives:;

Primary Master IDE: 40.0 GiB Maxtor IDE HD      /dev/sda
Serial ATA: 500 GiB Seagate Barracuda           /dev/sdb

The Maxtor currently has 3 partitions:

ext3   Linux Partition - "Main System"              /dev/sda1
ntfs   Windows Partition - "To Be Windows install"  /dev/sda2 
swap   Linux Swap Partition                         /dev/sda3

The Seagate currently has 1 partition:

ntfs   Windows Partition  /dev/sdb1  

If I were to try and install XP in the partition Linux sees as /dev/sda2, would Windows be able to see the partition and install in it? If it could, what would I have to do to make Ubuntu boot first using the GRUB boot loader? (since I assume that Windows will try to impose it's own stupid loader) 

Any help is appreciated.

---

### Post by Pumalite on 2008-10-25
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)
There are other threads in the Forum on the subject.

---

