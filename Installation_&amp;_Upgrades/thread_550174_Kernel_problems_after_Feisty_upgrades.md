---
title: "Kernel problems after Feisty upgrades"
date: 2007-09-13
forum: Installation &amp; Upgrades
---

### Post by tamu on 2007-09-13
I just applied updates to Feisty, one of which was a kernel update, and after rebooting I never get passed a grub>  prompt.  I've tried the boot command, which returns the error:

Error 8
Kernel must be loaded before booting.

I ran Memtest without problems, and then tried to rewrite my mbr with the following commands from another post:

grub>find /boot/grub/stage1
hd(0,0)

grub>root (hd0,0)

grub>setup(hd0)

grub>exit

I'm not sure that regenerating the mbr has anything to do with this error, but I tried it anyway.  I've tried defining the kernel to boot using the kernel command at the grub prompt, and specifying what I think should work from the /boot dir, but after the boot command the system hangs after reporting a kernel panic.  I've used Ubuntu exclusively for the past 8 months without any major problems (nothing that I couldn't solve reading others posts at least), and have updated the kernel several times.  Is there a way to resolve this without reinstalling Ubuntu?

---

### Post by dabl on 2007-09-13
From a console try ```
gksu gedit /boot/grub/menu.lst
``` and see which partition is listed right under the new kernel boot line -- this would presumably be the first kernel listed in the "Debian Automagic" part of that file, which is 2/3 of the way down.  It should say (hd0) and I'm guessing it might say something else, for some reason. So you can edit it, and "save", and exit, and it should boot the new kernel correctly.  (I'm crossing my fingers ...) :)

---

### Post by tamu on 2007-09-13
Thanks for the help dabl.  I edited the /boot/grub/menu.lst file and noticed that all of the kernel image config-blocks specified:

root=(hd0,0)  

However, there was a line commented out in the default config section:

groot=(hd0,0)

which was documented as the default grub root device.  I uncommented that line, rebooted, and voila, back in business.  Thanks again for the advice.

---

