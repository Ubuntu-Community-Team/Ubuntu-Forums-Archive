---
title: "Ubuntu Installation Problem"
date: 2007-06-12
forum: Installation &amp; Upgrades
---

### Post by torelativity on 2007-06-12
Hi! I had downloaded Ubuntu 7.04. I tried installing Ubuntu by Graphical Mode. The installation proceeds till 94% and stops saying Fatal Error: GRUB cannot be installed. This happened twice. First time, the default location for bootloader was (hda0) and second time I changed it manually to (\sda1)(sda1 being my vista partition)( I had changed it to sda1 because I could not find hda0 on my Manual Partition). Please Help me!

Also I had accidentally erased my recovery partition when trying to make a new partition for Linux and would want it to be back (I have created Recovery Disc too yet I would want my recovery partition because I cant rely completely on recovery discs). HP is unable to help me. I tried recovering my laptop back to its original factory settings but still I cant get my recovery partition back. Please help me!
PC Configuration:
HP Pavilion Notebook.
Windows Vista Home Premium pre-installed.
Architecture is i386.
2 GB RAM.
160 GB HDD.
Intel Core 2 Duo 2 GHz Processor.
Thanks in advance.

---

### Post by poohbear1616 on 2007-06-12
Just something that popped in my head that is worth a shot.
I have a compaq that came with vista which had basically the same set up.
Since compaq is made by  the same folks as hp I'm hoping this will be similar.
At the first boot screen several options are offered up by pressing F1,2,3..etc.
One of them is for restore which is started off from the bios without the disks.
I've used it once when I screwed up the dual boot and it fixed the boot record and
restores the system. BUT!!! I am assuming it was drawing off the recovery partition
which you are  refering to. It is worth a shot. Also if you have several partitions it will pick out 
the first primary partition to restore to instead of using the whole drive.
This was my experience and I hope it helps you.

---

