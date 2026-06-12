---
title: "Virtualbox Won't Mount Floppy"
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by HDTimeshifter on 2008-11-15
I installed Sun's .deb Virtualbox, but it won't mount my floppy drive and also gives me the following USB error when I try to mount it:

> Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.

Result Code: 
NS_ERROR_FAILURE (0x00004005)
Component: 
Host
Interface: 
IHost {489fb370-c227-4d43-9761-ceb28484fd9f}
Callee: 
IMachine {1e509de4-d96c-4f44-8b94-860194f710ac}

I don't know why it is trying to use USB when my floppy is connected as a traditional floppy/IDE device.

This is a critical error as I am unable to install Windows XP on Virtualbox since my XP install CD is not bootable and requires floppies to boot.

---

### Post by inobe on 2008-11-15
i don't know if this will help you, it bit of googling says you can create a boot cd for xp.

ypur probably want to fix the current problem, i assure you' the boot cd is faster.

example: fdisk' run the command ```
setup.exe
```

the ultimate boot cd has this ability, google will point you to many variations.

i hope i am offering some insight :)

---

### Post by cariboo on 2008-11-15
You can create a bootable cd using K3b. Coy all the files from your XP cd to a directory on your hard drive, then go here:

[http://www.bootdisk.com/bootdisk.htm](http://www.bootdisk.com/bootdisk.htm)

I downloaded the win98se custom image. Use file-roller to extract the image file (right click and select Open with Archive Manager)

Next open K3b and select New Data project. Click Project-->Edit Boot Images, click the New button and select the win98se image file you extracted. Click OK.

Add your win xp files and burn the CD. You now have a bootable Win XP CD. I'll leave the installation up to you, as there are about three or four different ways to do it.

Jim

---

