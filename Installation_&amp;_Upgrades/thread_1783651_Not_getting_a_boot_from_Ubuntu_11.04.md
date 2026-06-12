---
title: "Not getting a boot from Ubuntu 11.04"
date: 2011-06-16
forum: Installation &amp; Upgrades
---

### Post by someguynameddave on 2011-06-16
Hey all,

So, I just downloaded a fresh copy of ubuntu-11.04-desktop-amd64.iso, burned it, and gave the installer a whirl. It detects all my drives just fine:

- one IDE drive with an NTFS partition on /dev/sda
- one SATA, NTFS partition, with a bootable copy of WinXP64 on /dev/sdb
- one SATA with ext4, swap, and a boot partition on /dev/sdc
- one SATA, NTFS partition /dev/sdd

I use the installer to "erase and install" on the /dev/sdc SATA drive. When it's all finished, and I reboot my machine, it boots straight into windows. No grub or lilo boot menu. No signs of ubuntu existing in the system anywhere.

So, I tried disconnecting all but the drive with the newly installed ubuntu distro. Once it gets past all the mobo bias stuff, it looks like it's reading the drive for a minute, but then just hangs there with a blank screen, save for a blinking cursor. Just to be sure, I let it do its thing for an hour or so, but when I came back to it, it was still all blinky cursor. 

So, what might I be doing wrong, and how do I get it to boot the new install? And (eventually), I would like to dual-boot. Is there some special procedure to make that happen? It's been a while since I've installed a dual-boot system, but I seem to remember the installers being smart enough to detect other OSes and magically making a boot menu for me. 

Thanks for any help you can give.

Dave

---

### Post by sanderd17 on 2011-06-16
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

please follow this steps and report the result. GRUB is probably installed to the wrong disk.

---

