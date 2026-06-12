---
title: "Wont work"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by Royville on 2007-04-22
Hi 
I  Have Just Installed Fiesty With The Live Cd And When I Tried To Reboot It Just Hangs. All I Get Is The Nice Ubuntu Logo With A Tiny Segment Of The Progress Bar Turned Orange.
Please Help!

Thanks In Advance

Roy.

---

### Post by eyelessfade on 2007-04-22
try reboot, when you come to grub hit "e" for edit. In the first line hit "e" again. At the end remove the word "silence" and hit "enter" then "b"

now ubuntu will start with more output. when and if it halts again, write down the last lines and post them here.


Sorry for the not so intuitive howto

---

### Post by Royville on 2007-04-22
Hi,

Here are my last lines.

                         Check root= bootarg cat /proc/cmdline
                         or missing modules, devices:cat /proc/modules is dev
ALERT! /dev/disk/by-uuid/facd545e- etc-etc-etc does not exist. Droping to shell!

BusyBox v1.1.3  etc etc
Enter 'help' for list of built-in commands.

/bn/sh: can't access tty; job control turned off
(initramfs)

---

### Post by eyelessfade on 2007-04-22
auch not good. It might be the libata problem in the kernel lately.

When this have happened to me, a couple of reboots worked. Don't ask me why. seems that it don't always find the hard drive.

other then that I can't help you sorry. Hope someone else can help

---

### Post by Royville on 2007-04-23
Ok, thanks any way.

I also hope some one else can help me.

Roy.

---

