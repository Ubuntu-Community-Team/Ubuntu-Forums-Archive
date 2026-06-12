---
title: "Windows doesn't exist..."
date: 2010-04-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Usksider on 2010-04-15
Hi all.

A couple of days ago i sought help [retrieving Windows 7 following a Lucid Lynx installation]("http://ubuntuforums.org/showthread.php?t=1453278").

Having struggled for a week or so to get Windows back I finally gave up and reinstalled Windows 7 over the original partition today; I now have Lucid Lynx and Windows 7 sitting side-by-side and working perfectly... except for one small thing:

When I boot Lucid Lynx from the Grub menu it halts mid-flow and says the Windows partition/Windows doesn't exist. Choices are either to wait until the partition is ready, S to stop setting up the partition and continue booting, M to set up the partition manually.

I waited, but after 30 minutes got bored and pressed to continue loading Lynx. :(

Just to recheck everything was as it should be, I rebooted the computer and from the Grub menu loaded Windows 7 - perfect. :)

Rebooted again, selected Lucid Lynx and was presented with the same Windows partition/Windows doesn't exist. :confused:

I tried an update-grub
```
Found linux image: /boot/vmlinuz-2.6.32-21-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-21-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-20-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-20-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-19-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-19-generic-pae
Found linux image: /boot/vmlinuz-2.6.31-20-generic-pae
Found initrd image: /boot/initrd.img-2.6.31-20-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1

```Rebooted and same thing.

I tried repairing Grub from the Linux recovery mode: same thing.

Any ideas anyone?

---

