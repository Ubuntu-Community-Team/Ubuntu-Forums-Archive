---
title: "Natty Installer Does Not Detect My Hard Drive"
date: 2011-05-17
forum: Installation &amp; Upgrades
---

### Post by kerryhall on 2011-05-17
Natty standard installer does not detect my hard drive, but whatever disk utility that comes with the installer (gparted perhaps?) detects it fine.

Running off a raid controller that is integrated into my motherboard. nForce 4 chipset.

Should I report this as a bug? From gparted and gnome, the disks are detected and work fine, so I don't see why the installer can't find em.

Thanks!

---

### Post by Quackers on 2011-05-17
In the live cd desktop, try installing the kpartx package with synaptic.
See if things improve.

If gparted then sees the raid set you should create and format the required partitions in that first. The installer seems to fail at creating the partitions otherwise.

---

### Post by kerryhall on 2011-05-17
Thanks! I will try installing that package first. 

I already created the partition table and formated the whole drive as ext4 before trying to run the ubuntu installer.

It seems to me that if gparted handles it fine but the installer doesn't, then there is a bug in the installer.

---

### Post by kerryhall on 2011-05-17
Alright, I am actually running on my integrated SIL 3114 Raid controller on my Asus A8N SLI motherboard, rather than the nforce4 raid controller. 

Tried sudo apt-get install kpartx before running the installer, no luck. Detects my ide drives fine. Gparted detects the drives on my SIL 3114 controller fine. I can read and write to the drives fine in the live cd.

Thanks!

---

