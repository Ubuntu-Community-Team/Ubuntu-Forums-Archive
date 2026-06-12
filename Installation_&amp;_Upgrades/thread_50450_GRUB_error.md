---
title: "GRUB error"
date: 2005-07-20
forum: Installation &amp; Upgrades
---

### Post by tlthomas on 2005-07-20
Hello, 

I have an IBM ThinkPad T42 Pentium M 1.7 Ghz laptop. In order for me to install the Ubuntu, I used the System Rescue CD from [www.sysresccd.com](www.sysresccd.com) to change my NTFS partition to give me space to install. 

My partitions are now set for a 30GB NTFS for my XP SP2 Pro install & 8 GB free for my ubuntu. I was able to install everything fine including the GRUB to the primary (only) hard drive. I booted into ubuntu as well as into my XP install that already existed. 

My problem is that after a few reboots, my screen comes up with the GRUB 1.5 and instead of showing me the choices for OS's it cycles back to the initial IBM boot screen and continues to loop. I have tried reinstalling it 3 different times with the same results each time. Anyone have any ideas?

---

### Post by mingus on 2005-07-20
Don't have an answer, but this may be a clue . . . some laptops, I believe Thinkpads included, have a recovery partition and front-end code loaded from the BIOS that  controls bootstrap in order to get into recovery if needed.  It may be that this and grub are interfering with one another.  If someone else doesn't come up with an actual solution, you might try using W$ to chain-load boot to Ubuntu.  There is a over-complicated HowTo on this in the wiki, but all it really involves is (a) installing grub to the partition the Ubuntu /boot directory is on (usually same as /), (b) making a copy of the just created boot sector on that partition to media that can be read by W$, like a DOS floppy, (c) copying that file into W$ C:\ and then (d) adding a line to C:\boot.ini which references the file you just created on C:\

---

