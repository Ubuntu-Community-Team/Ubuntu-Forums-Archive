---
title: "Installing from Hard disk"
date: 2012-02-20
forum: Installation &amp; Upgrades
---

### Post by jana05 on 2012-02-20
Hello All, 

am returning to Linux distros installation after a very long time....I have an old system and "CD/FDD/USB Boot" don't work or not available. Hence my only option is to install from the hard disk....

I remember in the earlier days of linux 2.0x versions there used to be a method to install from the hard disk or a net install or a kickstart method....but the install from hard disk method does not seem to be available, and no help even after a long google search....Do we such a method available with ubuntu or other distros...?

Can somebody throw some light/links/directions towards installing from the hard disk...I tried the vmlinuz/initrd copy into "c:\boot" alongwith grub4dos-0.4.1 into "c:\boot\grub" and boot.ini modification, but this stopped at initramfs....tried this way with ubuntu, fedora, etc...none worked...

I am at my wits end to solve this installation issue....Help please!!!

Thanks in advance...

---

### Post by jana05 on 2012-02-21
Oops! No help on the current distros for installing from Hard disk?? Pushing it up...

---

### Post by mastablasta on 2012-02-21
assuming you checked and made sure that your system is compatible with latest kernel and meets the system requirements you can simply just install it to hard disk and then clone it to your old maschine disk.
 
or the other way arround. put the CD/USB in new mashicne, boot from it, install the OS to old disk (basic istall and mkae sure you put grub on this old disk) and then move the old disk back to the old mashcine. boot and enjoy.
 
i am not sure about ubuntu but debian has netinstal if that is what you are after.
[http://www.debian.org/distrib/netinst](http://www.debian.org/distrib/netinst)

---

