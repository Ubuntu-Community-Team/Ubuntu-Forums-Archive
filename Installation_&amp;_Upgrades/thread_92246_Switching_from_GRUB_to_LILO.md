---
title: "Switching from GRUB to LILO"
date: 2005-11-19
forum: Installation &amp; Upgrades
---

### Post by kinghajj on 2005-11-19
I have already installed Ubuntu 5.10 with GRUB as my bootloader; now I want to change it to LILO. I don't need to deal with multiple partitions; Ubuntu has its own hard drive. ;) 

Any help is greatly appreciated.
Thanks.

---

### Post by matthewv on 2005-11-19
Any reason you want to change??? I used to use LILO, but grub is all i need. 
I think, though, you need to install lilo, and then check the config file and set it up right, before running "lilo <device where you will install lilo>" eg "lilo /dev/hda" to install it to the mbr. I've never tried it though, so I wouldn't know for sure.

---

### Post by kinghajj on 2005-11-19
The reason I want to change is so I can get higher console resolutions (like I believe Knoppix does...) so I'm not stuck with 80x25. I tried SVGATextMode, and couldn't get that to work with my nVidia. The LILO method of "vga=ask" just seems really easy.

---

