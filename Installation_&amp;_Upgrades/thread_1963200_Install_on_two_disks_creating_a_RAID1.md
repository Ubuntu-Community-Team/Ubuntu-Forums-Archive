---
title: "Install on two disks creating a RAID1"
date: 2012-04-22
forum: Installation &amp; Upgrades
---

### Post by yarick on 2012-04-22
[edubuntu] Install on two disks creating a RAID1. Does anyone know how to do it?

---

### Post by darkod on 2012-04-22
Fakeraid or software raid?

For fakeraid (bios raid), you set up the array during boot, there should be a message to press some key to enter the setup. Then edubuntu should see it as a single raid device and simply install on it.

For software raid, you leave the SATA mode to AHCI in bios, and you can create the software raid during the installation.

I haven't used edubuntu so I don't know how the installer looks exactly.

---

