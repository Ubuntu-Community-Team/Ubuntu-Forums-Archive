---
title: "dual boot issues"
date: 2008-02-14
forum: Installation &amp; Upgrades
---

### Post by benniebrown07 on 2008-02-14
I installed ubuntu no problem and everything worked. I got curious and decided to try mandriva, so i installed it.
Ubuntu and Mandriva pops up on the grub menu, and i can start and use Ubuntu easily, but I cant start Mandriva the normal way. I have to start it from what I guess is safemode. Mandriva shows on my grub in three parts; the Normal one, Linux Nonfb, and Linux Failsafe.
 Linux Nonfb, and Linux Failsafe will startup and work pretty good. If i start the normal one it starts up saying booting the system and the status bar goes about halfway and then it jumps back and it says system shutting down and my pc cuts off. I had problems dual booting these two before, then i heard the install order can make a difference. This time its going alot better than before and everything is working but i cant access the music and videos (or anything else for that matter) I download from ubuntu  on mandriva and vice-versa. In the Storage Media app it doesnt even show the partition Ubuntu is on. I have a 80gb and its split about 50/50 between the two, but the Storage Media app only shows the mandriva partition. Ubuntu's files dont show up in Mandriva at all. Mandriva's files dont show up in Ubuntu either. Has anyone else had a similiar problem or did I do something wrong. Im still kinda new to linux.

---

### Post by EXCiD3 on 2008-02-14
In order to access the other OS's files you need to mount the partitions. In order to mount a partition you need the name of the partition in the /dev folder. Typically it will be named sdXX or hdXX (where the first X is a letter of the alphabet and the 2nd X is a number)

Then open terminal and do the following commands
```
 mkdir  /mnt/mandriva
mount  -t ext3  /dev/????  /mnt/mandriva
```

The first command creates a directory to allow access to the partition and then second mounts the partition to that folder. You can modify the "/mnt/mandriva" to whatever folder you like. "/dev/????" is the file mentioned above (partition of your mandriva installation).

This will only help you mount mandriva in ubuntu. Mandriva may be slightly different, maybe not, ive never used it. Hope this helps somewhat!

---

### Post by benniebrown07 on 2008-02-14
I put these in the in the terminal and it put disk on my desktop and when i open it and try to open the home folder i get:
The folder contents could not be displayed.
You do not have the permissions necessary to view the contents of "bennie".
 
When I open the lost & found folder it does the same thing but the guest folder opens but it shows ubuntu's files. I was skeptical so I compared the disk's free space and there different. So I guess that disk on the desktop is mandriva but i just cant view whats in it. Suggestions?

---

