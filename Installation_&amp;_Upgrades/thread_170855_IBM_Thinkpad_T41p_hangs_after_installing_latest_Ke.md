---
title: "IBM Thinkpad T41p hangs after installing latest Kernel fixes"
date: 2006-05-05
forum: Installation &amp; Upgrades
---

### Post by MikeFoxtrott on 2006-05-05
After installing the latest updates yesterday (04 may 06), my Ubuntu 5.10 doesn't boot correctly into kernel 2.6.12-10-386. GRUB stops with error messages. Fallback to 2.6.12-9-386 works. I had 2.6.12-10-386 already working, very stable by the way. What can I do to get the latest patch up and running?

Please help!

---

### Post by ajgreeny on 2006-05-05
Have you checked that your /boot/grub/menu.list file is correctly pointing to the new kernel, ie are the numbers at the end of the new listing for the kernel correct and in the same format as the old kernel?  If that doesn't help then I'm afraid someone else will have to assist.

---

### Post by MikeFoxtrott on 2006-05-05
/boot/grub/menu.list is fine. It must be, since I had this kernel already before applying the last update.
Grub stops with Error 18 which is very strange. The BIOS is not touched, the harddisk the same, no changes in the boot loader config manually.

I am a little bit upset :-( Could anybody from Ubuntu support give advise.

---

