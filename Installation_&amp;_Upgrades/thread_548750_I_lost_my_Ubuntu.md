---
title: "I lost my Ubuntu"
date: 2007-09-11
forum: Installation &amp; Upgrades
---

### Post by Uncle Gates on 2007-09-11
I installed sabayon to see if I would like it. It turned out ok, but it sucked all my resourses...
I tried going back to Ubuntu but the grub loader did not pick it up. I need back ubuntu...
What should I do?
The sabayon boot loader uses grub2

---

### Post by Pumalite on 2007-09-11
Re-install Grub:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Uncle Gates on 2007-09-17
I can't Install Grub. I already have grub 2 installed. I just need the kernel boot path and intrid location and anything else I need to load from grub to start it. I placed a kernel boot path and intrid location and ubuntu started loading but it never passed the boot screen.

---

### Post by dabl on 2007-09-17
The /boot/grub/menu.lst file in your Ubuntu root partition should have the correct boot path and file names that you need for the grub 2 menu file.  :)

---

### Post by Uncle Gates on 2007-09-17
> **dabl said:**
> The /boot/grub/menu.lst file in your Ubuntu root partition should have the correct boot path and file names that you need for the grub 2 menu file.  :)

I did that originally, but the boot screen only starts, it does not load though.:(

---

### Post by dabl on 2007-09-17
How about the so-called "boot options" on that kernel line?  noacpi, nolapic, etc.

---

### Post by Uncle Gates on 2007-09-17
I have no idea what those terms mean, is that in the command line?

---

### Post by Pumalite on 2007-09-17
Here is a collection you can choose from:

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)

[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO-3.html](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO-3.html)

---

### Post by Uncle Gates on 2007-09-20
I removed the sabayon partition in windows. The computer won't start now. It said grub 1.5 error. Can I use the live cd now?

---

### Post by Pumalite on 2007-09-20
Use Super Grub to boot Ubuntu and fix Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

[http://users.bigpond.net.au/hermanzone/p15.htm#Grub_loading_stage1.5](http://users.bigpond.net.au/hermanzone/p15.htm#Grub_loading_stage1.5)

---

