---
title: "USB Boot on Surface 3 not working"
date: 2015-10-31
forum: Installation &amp; Upgrades
---

### Post by farazoman on 2015-10-31
Hi, I wanted to install a dual boot on my surface so I installed 15.10 onto a USB and attempted to boot into the installer. I got into GRUB, then selected install but then I got an error that flashed saying "no controller found". 

So then I though of maybe using 14.04, it seemed to be working better but it just never turned on. Again I had errors flash, I took a pic but is barely readable but this is my interpretation of them: 
1. No controller found
2. ACPI PCC cache failed
3. No dumping node page found
4. Assuming drive cache: write

There is code associated but it is barely readable

Just wanted to mention what I did before hand:
I had a partition of 24gb.
I disabled secure boot from bios.
I disabled hibernate.
I installed the bootable onto a sony 8gb usb
I am also running Windows 10 with 4gb ram on Surface 3 (NOT the Pro)

I hope someone can help, I've tried looking all over online and to no avail, well the solutions I found didn't really work. Hope you can help.

---

### Post by oldfred on 2015-11-01
Do not know about Surface and differences between 3 and pro 3

[h=1]**[SIZE=1][FONT=arial]Ubuntu on Surface 3 (Non Pro)[/FONT][/SIZE]**[/h]http://0nit.com/?p=215

But another thread on Surface Pro 3.
[http://ubuntuforums.org/showthread.php?t=2231207](http://ubuntuforums.org/showthread.php?t=2231207)

---

### Post by DK1993 on 2015-11-02
I would stick to 15.10 because the Linux Kernel associated with 15.10 has updated modules for handling the newer hardware. 

Follow the advice given to get it to boot on LiveUSB in the link from previous post (0nit)

---

