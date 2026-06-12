---
title: "Really need help with Ubuntu installation"
date: 2016-02-04
forum: Installation &amp; Upgrades
---

### Post by Marco_Antonio on 2016-02-04
So, I've been trying to install Ubuntu 15.10 again on my desktop, but I keep getting multiple errors, trust me, I've tried every possible way to make a bootable USB flash drive (sorry I didn't mention before). Right now I can't burn a DVD neither read one, because my DVD reader broke, so I HAVE TO make a bootable usb device. I used unetbootin, Win32DiskImager (but i'm not sure if I used it's full potential), Universal USB Installer a few times and another program wich I don't remember the name.
I keep getting different errors every single time.
The info you need: 

MSI H87-G43 MILITARY CLASS
I5 4670 (3.3 gHz if i'm not mistaken)
4GB RAM
GTX 550 Ti 1GB VRAM
Windows 7 Ultimate 64bit

I'd really enjoy if you guys could help me.
I thank every one of you in advance.

---

### Post by Vladlenin5000 on 2016-02-04
Hi and welcome.

> **Marco_Antonio said:**
> I keep getting different errors every single time.
OK, would you mind giving more details, examples of the errors, ... ?

---

### Post by Marco_Antonio on 2016-02-04
I'll list a few of them, but almost every time I get a different, I think the most commons are these:    isolinux.bin missing or corrupted; invalid magic number;   could not find kernel image: linux.
So i will boot again and report the error that I'll get this time and the USB burner that i'll use
btw thank u for the quick response

---

### Post by Vladlenin5000 on 2016-02-04
Have you tried a different USB stick? Considering those errors that's the first thing I would do, that and try different USB ports, of course... And if you're doing it from Windows then I'd recommend [Rufus]("https://rufus.akeo.ie/").
Now, with Rufus, you'll notice the "Partition scheme and target system type" in which, assuming you want dual-boot with Windows 7, you should choose accordingly to how Windows 7 has been installed* - MBR/Legacy (BIOS) or GPT/UEFI.

* It depends on the UEFI settings -and- the type of media you used to install Windows: If DVD then Legacy.

---

### Post by Marco_Antonio on 2016-02-05
So...
I actually used Rufus 2.6.818 , and i'll describe how I configured it.
I chose MBR Partition for BIOS or UEFI, formatted it on FAT32.  Used Ubuntu 15.10amd64 iso
When I hit start, it said that the version which I had didn't have the needed files, so I pressed download and install and it started doing its job.

I rebooted it and had to take the flash disk out and put it back, because the mobo hadn't recognized it before, so I finally came to the error "Failed to load ldlinux.c32"

As for the dual boot and windows installation I don't know much, but if it's necessary, I would remove windows and use only Ubuntu

---

### Post by Vladlenin5000 on 2016-02-05
Again, that USB stick seems busted. And you should verify your download, Rufus complaining of missing files is NOT normal.

---

### Post by mastablasta on 2016-02-05
on windows - use H2testw or  Check Flash 1.16 maybe also Microsoft USB Test Tool (MUTT) , USB Flash Drive Tester (I used this one) to test the USB. if all is good you then need to check the md5sum of downloaded file [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by marcoantoniopc2000 on 2016-02-07
got it, guys.
I bought a san disk 8gb flash drive and managed to boot fine, thx for the help

---

