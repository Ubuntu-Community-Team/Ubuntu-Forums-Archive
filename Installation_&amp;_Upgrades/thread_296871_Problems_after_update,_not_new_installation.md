---
title: "Problems after update, not new installation"
date: 2006-11-10
forum: Installation &amp; Upgrades
---

### Post by ernster on 2006-11-10
This morning, I booted my laptop up and ran into a problem. This is not a new install (been running fine for about 6 mths), and I have kubuntu on top. Yesterday, I applied some updates (2 were available) and then shut down the system. Something has changed.

While loading the kernel, it tries to mount root and fails, then drops into ash for me to make changes if necessary.

The messages I get are:

mount: Mounting /dev/hda2 on /root failed: No such device
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mountin /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

Then it drops to BusyBox v1.01, with one last error message that says "/bin/sh: can't access tty; job control turned off

Then prompt.

I went into Grub's boot commands and found these commands:

"root (hd0,1)
kernel /boot/vmlinuz-2.6.15-27-386 root =/dev/hda2.ro quiet no splash
initrd /boot/initrd.img-2.6.15-27-386
savedefault
boot"


BTW: When I cd to /dev, there is an entry for hda2.

Any thoughts on this?

A bit about me: I am not exactly a Unix n00b, but I am definately a n00b when it comes to the guts of Linux, and it's been so long since I've had to do anything at this level, I'll need some hand-holding.

---

### Post by ernster on 2006-11-10
Also, booting into XP Pro through GRUB still works just fine, so I don't think it's a physical disk issue.

---

