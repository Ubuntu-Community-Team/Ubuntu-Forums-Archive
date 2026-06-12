---
title: "Yet another Virtual Server 2005 question - but probably VERY easy"
date: 2007-01-17
forum: Installation &amp; Upgrades
---

### Post by jimwillsher on 2007-01-17
I've installed Dapper under Virtual Server 2005 R2. 

During the boot up all the text is the wrong size, and I can only see half the screen. It's fine on the BIOS settings, but then "jumps" to the wrong text size during boot up.

Now, I've seen various references to editing x11.conf. However I'm not running any graphical interface on my server, I'm just running a LAMP install. So I'm not sure it's the right solution.

Anyone?

Many thanks,



Jim

---

### Post by jimwillsher on 2007-01-17
Answering my own post. The details are here:

[http://songhaysystem.com/document.php?kbDoc=unix_2076071762](http://songhaysystem.com/document.php?kbDoc=unix_2076071762)


> The foremost issue is getting the console display to appear correctly in Virtual PC 2004. Edit /boot/grub/menu.lst to change the first entry in the list of Automagic Kernels such that:

    kernel /boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro quiet splash

becomes

    kernel /boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro quiet splash vga=0x314

You can also hit ESC during the GRUB boot sequence and set vga=0x314.



Jim

---

