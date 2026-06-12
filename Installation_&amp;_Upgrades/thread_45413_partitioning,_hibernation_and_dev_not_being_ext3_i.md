---
title: "partitioning, hibernation and /dev not being ext3 issues"
date: 2005-06-30
forum: Installation &amp; Upgrades
---

### Post by amohanty on 2005-06-30
Hi All,

I have a tiny problem. My install works perfectly, with a couple of hitches. My partition details:
2 x 80G barracudas.
drive 1. WinXp 30.0G NTFS
             /boot    0.5G ext3
             /          rest    xfs

drive 2. swap    4.0G
             /home  rest  xfs

bootloader: grub

Now the problem if you can call it that is 
1. during bootup I get the message:
  ext3 fs not found on sda5, mounting tmpfs on /dev
  Does that mean I will need an ext3 /dev/ partition as well?

2. I also get this message:
  Cannot connect to Hardware clock using any method.
  Any idea why this happens and how to fix it?

I also had a question regarding hibernation. In suse you can specify a partition of type 0x8... type that is used for hibernation only, now when I select logout from the system menu, I get the hibernate option. So where does the system hibernate to?

Thanks.

AM

---

### Post by tonym on 2005-06-30
"ext3 fs not found".  I suspect that in /etc/fstab you have / defined as auto.  If so it seems to try ext3 first and then when that doesn't work it tries other types until it decides it is xfs.  You don't need to do anything.

"cannot connect to hardware clock"  This is a known problem.  If you look further down the boot it probable does connect later.  Again ignore.

Can't help on hibernation.

---

### Post by amohanty on 2005-07-01
Thanks a ton tony.

---

