---
title: "Create currect OS full image and use it as virtual machine."
date: 2013-11-05
forum: Installation &amp; Upgrades
---

### Post by cpu2007 on 2013-11-05
I have decided to make windows 7 as my primary OS because there are too many compatibility issues and support using ubuntu as a primary os. However, I still wanna keep the OS as I have software, apps and development tools that I'd like to keep using them on ubuntu instead of windows.

Currently my primary OS is ubuntu 13.04 on a samsung series 7 chronos, with the root on an sd partition and the home on a harddrive.

Is it possible to make a full image of my system so that after I can wipe everything ,install windows 7 as primary os and in a virtual machine load the ubuntu image I created, so that I don't have to go through all the settings again.

Thank you

---

### Post by Dreamer Fithp Apprentice on 2013-11-05
I think you could do it Clonezilla. If you use it I think the easiest way would be to boot from a Clonezilla CD, image your ubuntu storing the image on some other partition, and later boot the VM in Windows from a Clonezilla iso (or alternately the hardware CD drive) and restore the image. There are other ways to use Clonezilla, and other imaging products, notably including fsarchiver if the system is on ext3 (but not ext4 or something exotic) that could be made to work but I suspect Clonezilla will be the easiest.

Or, if you want a challenge, it should be possible to shrink the ubuntu partition, making enough room for Windows at the biginning of the drive (cause I think Windows is kind of picky about where it is installed), install Windows, restore grub after Windows assasinates it, thus having dual boot potential. Now would come the tricky part. I haven't done it but it should be possible and would be fun to try. I think you might be able to set up a VM in windows that would boot off the Ubuntu partition of the hard drive so that you could boot it either natively OR in a vm in Windows. I read about a fellow doing something very similar although not with that particular OS combo. If you try that I'd be interested what kind of result you get.

---

