---
title: "How to do custom LVM with encryption"
date: 2014-04-23
forum: Installation &amp; Upgrades
---

### Post by fde2 on 2014-04-23
I don't know about everyone else, but I think that Ubuntu has degraded itself by removing the ability to do custom LVM + encrypt during install. Why they decided that they should make it impossible to do this is anyones guess. With UEFI you can't even use the small CD to try it. There are tutorials on how to do custom LVM + Encryption during install, but they are very involved and will scare most people away. Thankfully it is still possible to do what you want! 

During the normal install from the live CD, simply select to use encrypted LVM and let the Ubuntu installer randomly guess at how you would have configured it yourself if they thought you should be able to have control over your own parition table. Install as normal.

After the installation is complete, reboot back into the live CD. Install system-config-lvm and run it. For me I had to mount the encrypted virtual drive, which is as simple as double clicking the icon on the desktop and entering the password in. Now system-config-lvm can detect it. Delete swap if you don't want it, I have an abundance of RAM and a small SSD so I don't want any swap space at all. Now you need to actually unmount the drive, which is as simple as right clicking on it and going to unmount. Now you can resize the the root partition to whatever you want. You can now use the remaining free space to configure the LVM how you wanted to configure it during installation, but were not allowed to because the Ubuntu installer thinks it knows best.

When you are done, simply reboot into your installed OS.

---

