---
title: "Grub fails to install when booting from USB (ubuntu 12 install)"
date: 2014-04-05
forum: Installation &amp; Upgrades
---

### Post by a-converted-sparky on 2014-04-05
Hi Guys,

Simple question, with i hope a simple answer  - this is driving me made!

I have created a usb ubuntu install (12.4) to install on my machine (none efi) however during installation the installer detects the MBR on the USB drive itself and marks it as /dev/sda and my hard drive is then /dev/sdb

When it comes to installing grub later in the install, it fails to install to /dev/sda as this is the USB drive.

Do i need to run the install with an argument or something? - i created the install from pendrivelinux creator download


Please help :P

---

### Post by Kris_Spencer on 2014-04-05
That is odd. I also had an issue with Grub installing, but I used a DVD. I just told it to skip it when it asked me what to do about it. When the install was complete, I told it to continue testing Ubuntu and I manually installed Grub with no problem. If you would like to follow that procedure:

These commands assume that root is on /dev/sda2 and boot is /dev/sda1. Change these accordingly!

Open terminal:

```

sudo -s
mount /dev/sda2 /mnt
mount /dev/sda1 /mnt/boot
mount -t proc proc /mnt/proc
mount --rbind /sys /mnt/sys
mount --rbind /dev /mnt/dev
chroot /mnt /bin/bash
source /etc/profile
grub-install /dev/sda
exit

```

That should do it.

---

