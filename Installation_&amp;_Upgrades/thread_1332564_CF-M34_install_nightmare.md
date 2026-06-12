---
title: "CF-M34 install nightmare"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by sunnovah on 2009-11-20
Trying to install Jaunty on a CF-M34. I think I finally figured out a way to do it. I have an 800MB partition with the Jaunty Live CD copied over. I used the cp -a command to accomplish this.

I am following the [https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux) guide to try and install it from a partition once I have the hard drive in the M34.

I have edited the /boot/grub/menu.lst with
[FONT=monospace]
[/FONT]title         installer[FONT=monospace]
[/FONT]root                   (hd0,0)[FONT=monospace]
[/FONT]kernel     /casper/vmlinuz boot=casper root=/dev/ram ramdisk_size=1048576 rw[FONT=monospace]
[/FONT]initrd                /casper/initrd.gz

However whenever I use the grub menu to boot to Installer I get taken to a "(initramfs)" prompt.

How do I access the wubi.exe file so that I can actually install ubuntu onto this drive?

I installed Ubuntu while the drive was in a CF-51 and it works fine there, but when I put the hard drive in the CF-M34 It won't display anything. :(

---

