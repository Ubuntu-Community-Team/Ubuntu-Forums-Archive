---
title: "Boot-repair failed, when i boot, cryptsetup immediately sleeps"
date: 2021-05-14
forum: Installation &amp; Upgrades
---

### Post by rich974 on 2021-05-14
Hi,

A day ago I started to have an issue that when I booted, it immediately booted to some weird terminal. I used a live-usb to boot into and start trying to reinstall grub and do various other things (on the boot partition), I then ran the boot-repair tool, and pasted the output here:

[https://paste.ubuntu.com/p/RRhswgPD5M/](https://paste.ubuntu.com/p/RRhswgPD5M/)

Summary: I have an encrypted partition on sda3 which is my linux root, my boot partition is on sda2, and the main efi thing is on an ssd.

I'm pretty sure this whole thing started because i removed some old kernal from the boot partition (it was 300mb and kept getting full, when i ran upgrade it always complained, I've now repartitioned it to 1gb)
I ran the recommended repairs, and that did actually make GRUB display ubuntu and windows, but when I selected ubuntu, it immediately goes to the "cryptsetup: going to sleep for 60 seconds".
I tried booting in recovery mode, and it gives /sbin/cryptsetup not found. I've tried looking around on how to fix this, but got nowhere.
After saying that and just before going to the busybox initramfs command propmt, it says "ALERT! UUID=4e882a9... does not exist. Dropping to shell!
I tried chrooting on the live usb (mounting all the things properly, effectively following the first answer here and modifying it to work with my system [https://superuser.com/questions/614257/how-do-i-recreate-a-wiped-boot-filesystem-in-ubuntu](https://superuser.com/questions/614257/how-do-i-recreate-a-wiped-boot-filesystem-in-ubuntu)) and running update-initramfs -u as suggested somewhere, but that fails.
I (before running the tool) tried doing update-grub manually, but that made only windows display, and it doesnt even find ubuntu

I know I can reinstall, but that is a huge time-sink and if I'm able to fix it without doing that, I'd prefer to.
Any help on how to fix this appreciated

---

### Post by TheFu on 2021-05-16
Long descriptions, but no actual commands.  We need to see the commands, in order, to be much help. You didn't mention setting up a chroot at all. That's needed to properly update-grub.

boot-repair hasn't really worked in a few years with non-trivial setups.

If it were me and I'd spent over 30 minutes trying to fix it and failed, I'd do a fresh install of a minimal system, then restore from my backups.  In 45minutes, my system would be back like it was previously.  Whenever encryption is used, having excellent backups is mandatory.

---

### Post by oldfred on 2021-05-16
Boot-Repair will work with encrypted install, if you manually mount & decrypt your install before having it update grub.
It will not work if you have partitions for folders typically in / as it only looks for /boot as another partition to mount.
Otherwise you have to do a full chroot & be sure to mount esp, /boot & / after decryption.

---

