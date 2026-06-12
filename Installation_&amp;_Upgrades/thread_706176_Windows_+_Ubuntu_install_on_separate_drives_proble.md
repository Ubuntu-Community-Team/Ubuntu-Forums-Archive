---
title: "Windows + Ubuntu install on separate drives problem"
date: 2008-02-24
forum: Installation &amp; Upgrades
---

### Post by digitaldave on 2008-02-24
I'm having a bit of a problem installing XP and Ubuntu on a system with two separate drives... I have XP already installed on the system's main SATA drive, and I have a spare old IDE drive that I want to install Ubuntu on to. I ran the live CD and did the install to the correct drive (the IDE one), but when I reboot, I don't get the GRUB prompt asking which OS I want to boot in to :(. I have a feeling it may be something to do with how I have the IDE drive set up - it's currently set as a slave drive on the secondary IDE channel. The only other IDE device is the DVD drive, that's the primary channel master drive.

Does anyone know what I've done wrong?

Thanks,

Dave.

---

### Post by digitaldave on 2008-02-24
Never mind, I found out how to fix it - I needed to change the BIOS settings for which drive to boot from first, i.e. the IDE drive with Ubuntu installed on it. Everything works fine now :).

---

