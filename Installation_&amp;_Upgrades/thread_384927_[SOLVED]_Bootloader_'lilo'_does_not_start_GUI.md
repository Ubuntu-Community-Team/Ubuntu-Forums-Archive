---
title: "[SOLVED] Bootloader 'lilo' does not start GUI"
date: 2007-03-15
forum: Installation &amp; Upgrades
---

### Post by Cariboo1938 on 2007-03-15
Hi all,
I run Ubuntu 6.10-amd64, kernel 2.6.17-11-generic, NVIDIA Driver Version:1.0-9755.
I installed lilo and after executing ```
sudo /sbin/lilo
``` to finish the installation I got this message > Warning: Unable to determine video adapter in use in the present system.
Warning: Video adapter does not support VESA BIOS extensions needed for
  display of 256 colors.  Boot loader will fall back to TEXT only operation.
Added Lin_2.6.17img0 *
Added Lin_2.6.17img1
Added Memory_Test+
root@BitByters-Desktop:~#
When I restart the system, using my GAG47 boot floppy---- which uses lilo to boot the system---- I only can get only to the TEXT mode.

When I use GRUB for rebooting everything works fine.
Has somebody an idea what might be wrong?

---

### Post by Cariboo1938 on 2007-03-17
Problem solved! 

I had to change the sequence in the menu.lst.
Lilo uses the first kernel it finds in the menu.lst and this was in my case the old 
kernel 2.6.17-10-generic which does not work with the newest nvidia driver. 

Case closed!:guitar:

---

