---
title: "USB pen drive install Gutsy Gibbon and persistence problem"
date: 2007-11-23
forum: Installation &amp; Upgrades
---

### Post by brokenbones on 2007-11-23
Hello,

As many others, I am in trouble with setting up Ubuntu on a USB flashdrive in a persistent configuration from the LiveCD. I tried both the pendrivelinux and the Ubuntu wiki methods, and both fails with the same problem: mounting the second partition. I tried 2 different sticks (different manufacturers, different capacities).

The installation works fine, as does booting from the USB flashdrives, but persistence doesn't work. I found that the second partition on the USB flashdrive, needed for persistence, cannot be mounted when booting from the USB flashdrive itself, but appears and is accessible normally when booting from the LiveCD or another Linux session. When booting from the USB stick, there is only one USB icon on the desktop, and it's the Fat16 "Ubuntu 7.10" partition.

gparted sees the ext2 partition called "casper-rw", but when asking for the partition properties, gparted says the partition could not be mounted because no mountpoint was found. Trying to edit this partition will crash gparted.

Without persistence, a live session from USB is easy to carry around, but having to set up the keyboard and wlan security on every boot is a real nuisance. Moreover, I am stuck with a resolution of 1280x1024 on a 20" TFT designed for 1600x1200, and without persistent drivers I cannot reach that resolution. Otherwise 7.10 looks and performs great... 

Any help ?

Lorenzo

---

