---
title: "Kernel Panic after installing Feisty"
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by cpd2007 on 2007-04-29
Im trying to install 7.04 Fiesty on an old Compaq Presario 7360 with 184mb RAM and 500Mhz AMD K6 Processor. I tried using the alternate installation CD, but it wouldn't work. It would either fail to install the kernel or stop at a certain point during installation, so I used the desktop CD.

Installation went smoothly, and I restarted, but was presented with a nice kernel panic. It states "Invalid compressed format (err=2)" and "not syncing: unable to mount root fs on unknown block (0,0)"

I tried a cheat code I found when I installed Edgy Eft which follows:

mkdir /mnt/linux 
mount /dev/hda1 /mnt/linux
chroot /mnt/linux /bin/bash
mount -t proc /proc /proc
sudo update-initramfs -u

Edgy started up fine afterwards, But it didn't work for Feisty, as I get the same kernel panic.


Any suggestions? Prompt feedback is appreciated.

---

### Post by cpd2007 on 2007-04-30
bump

Can someone help? I also tried installing Xubuntu to no avail. Same kernel panic.

---

