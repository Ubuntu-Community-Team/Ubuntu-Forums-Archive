---
title: "GRUB Installation Problem and recovery partition"
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

### Post by Pumalite on 2007-06-12
> **torelativity said:**
> Hi! I had downloaded Ubuntu 7.04. I tried installing Ubuntu by Graphical Mode. The installation proceeds till 94% and stops saying Fatal Error: GRUB cannot be installed. This happened twice. First time, the default location for bootloader was (hda0) and second time I changed it manually to (\sda1)(sda1 being my vista partition)( I had changed it to sda1 because I could not find hda0 on my Manual Partition). Please Help me!

Also I had accidentally erased my recovery partition when trying to make a new partition for Linux and would want it to be back (I have created Recovery Disc too yet I would want my recovery partition because I cant rely completely on recovery discs). HP is unable to help me. I tried recovering my laptop back to its original factory settings but still I cant get my recovery partition back. Please help me!
PC Configuration:
HP Pavilion Notebook.
Windows Vista Home Premium pre-installed.
Architecture is i386.
2 GB RAM.
160 GB HDD.
Intel Core 2 Duo 2 GHz Processor.
Thanks in advance.

During installation, 7.04 gives the opportunity of choosing where to install GRUB ( through 'Advanced' tab). I chose hd0,0.

---

