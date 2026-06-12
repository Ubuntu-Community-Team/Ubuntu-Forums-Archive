---
title: "Weird multiple disks mapping problem!"
date: 2008-11-29
forum: Installation &amp; Upgrades
---

### Post by zdude on 2008-11-29
I have a server that I have updated from 6.06 to 8.04. It contains a raid hardware card (3ware), four IDE drives and three SATAs. I noticed that /dev/HDx drives not not used anymore and every drive is now mapped to /dev/SDx and here is where my problem lies. Every time I reboot, my drives are randomly re-mapped. So my raid become SDG1 from SDA1, etc. I reboot again and then it flips it again to some other random dev id. I use UUIDs in my fstab for every device I mount but for some reason on boot if the devices are remapped it will stop booting and  complain about a disk failure when there is none. It seems as if it gets confused. Eventually, I reboot and it accepts whatever the mapping is :confused:
Can you put a device map file somewhere that Ubuntu will see on boot and map the drives according to UUID? Otherwise this is driving me nuts!

---

