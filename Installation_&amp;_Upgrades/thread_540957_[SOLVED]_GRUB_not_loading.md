---
title: "[SOLVED] GRUB not loading"
date: 2007-09-02
forum: Installation &amp; Upgrades
---

### Post by Apothysis on 2007-09-02
Hi,

I just installed Ubuntu 7.04, and everything installed fine (it seemed). But after the restart, I come to a dead point when it says "GRUB loading, please wait". It just goes on and on like that, I've tried waiting for half an hour, same thing.

When I boot with the Live CD and do the install once again, I notice that somehow the installation ignored my mount point choices. For instance, it changed "/" to "/media/sda1", and "/home" to "/media/sda3". Why does this happend? And when I access the HDD through the Live CD-version, I find that there is no GRUB-folder in the boot-folder. I've tried reinstalling several times, so that's how I know where the GRUB-folder is supposed to be.

During all installations, I've had the same problem with the mount points, and it gets stuck on the same place even when the GRUB-folder exists.

Also, I'm not dual-booting! I want to run Ubuntu only.

---

### Post by Pumalite on 2007-09-02
If you have no access to an OS, boot from Live CD, mount your filesystem and post: sudo fdisk -lu (copy and paste in the Terminal)

---

### Post by Apothysis on 2007-09-02
Wow this is odd. I decided to give a go at changing to my other HDD, the one from my old PC with Windows XP. It refused to boot as well. So I decided to remount the newer HDD and clear my CMOS just in case. Somehow, I successfully got the system to boot. Odd. Specially odd seeing as how the settings in BIOS are the same as before.

---

### Post by Pumalite on 2007-09-02
Use the 'Tools' and mark it solved then

---

