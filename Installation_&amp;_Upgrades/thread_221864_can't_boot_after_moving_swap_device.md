---
title: "can't boot after moving swap device"
date: 2006-07-24
forum: Installation &amp; Upgrades
---

### Post by didi156 on 2006-07-24
I deleted the swap partition and created a new one insinde an extended partition. So, now it's on sda5 while before it was on sda4.
Now on booting Ubuntu hangs when it tries to mount the local filesystems. I tried the rescue boot method, then I get more information. There's a kernel panic because of some wrong I/O access. Two lines before this it wants to mount /dev/sda4 as swap.

I have formatted the new swap device (mkswap /dev/sda5) and changed the entry in /etc/fstab to /dev/sda5. Now I'm wondering which configuration file still tells the kernel to use sda4 as swap device. It seems not to be specified in boot parameters.
Any ideas?

---

### Post by richbarna on 2006-07-24
Someone else sorted out a swap device problem like this :-
> **0.** If you haven't booted yet, use Grub's handy features to edit the boot command (press 'e', and read the instructions on the bottom. You should add "resume=/dev/hdxx" in the end of the line that begins with "kernel".
**1.** Edit "/etc/mkinitramfs/conf.d/resume" (needs sudo) to contain the right device address.
**2.** Run "sudo dpkg-reconfigure initramfs-tools" and wait a moment (it took about a minute for me, with one kernel installed).
**3.** Reboot, rejoice and start breathing again. (If it doesn't work, check the spelling everywhere, most of the stuff is case sensitive.) 
[From this thread]("http://ubuntuforums.org/showthread.php?t=159309")


Also take a look at the GRUB link in my sig.
|
|
v

---

### Post by didi156 on 2006-07-24
thanks alot, i'll try asap!

---

