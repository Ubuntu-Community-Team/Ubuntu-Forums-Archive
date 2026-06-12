---
title: "Disk boot failure - usb install"
date: 2011-01-20
forum: Installation &amp; Upgrades
---

### Post by Qifor on 2011-01-20
Hi, I am new to Ubuntu outside of some quick pokes around live cds over the last few years but I now have a spare computer mackled together from 2 broken ones. I am trying to install Ubuntu 10.04.1 on it to have a more indepth mess and maybe turn into something more.

One of the problems is it has no optical drive installed so I cant install via cd. I have tried using both the universal usb installer and unetbootin however both of these simply result in the error "Disk boot failure, insert system disk and press enter" when attempting to boot from a usb drive.

If anyone could offer some advice I would really appreciate it.

---

### Post by Quackers on 2011-01-20
Welcome to UF :-)
Have you changed your bios settings so that the usb flash drive boots before the hard drive?

---

### Post by presence1960 on 2011-01-20
Quite a few BIOS's recognize a flash disk as a HDD. Go into BIOS and check what Quackers asked you to check. While in there check under hard disk boot order and see if your usb is listed in there. if it is move it up to #1 position, save changes to CMOS and continue booting.

---

### Post by Qifor on 2011-01-21
I have set removable as #1 in the boot order and under HDD only the hard drive and a multi card reader is listed. Ive been using the rear usb ports not those on the reader just in case anyway.

---

### Post by presence1960 on 2011-01-21
At this point I would try booting the USB from another machine to see if it is the USB that you made that is the problem.

---

### Post by Qifor on 2011-01-21
I tried it on my current computer and although the name of the usb was displayed it continued and booted from the HDD.

---

### Post by presence1960 on 2011-01-21
> **Qifor said:**
> I tried it on my current computer and although the name of the usb was displayed it continued and booted from the HDD.

Sounds like the flash disk is no good! Try another flash disk or recreate another image on the current one after formatting it as FAT32.

---

### Post by Qifor on 2011-01-21
This is the only one I own thats big enough, the rest are all 1GB.

I have tried both universal usb installer and unetbootin, both using the programs formatting option and manually formatting as FAT32.

---

### Post by presence1960 on 2011-01-21
> **Qifor said:**
> This is the only one I own thats big enough, the rest are all 1GB.

I have tried both universal usb installer and unetbootin, both using the programs formatting option and manually formatting as FAT32.

1 GB is plenty- the image is 686 MB for 10.04.1

---

### Post by ronnielsen1 on 2011-01-21
[http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/)

[http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/)

You could try one of these. I've always had them work

---

### Post by Qifor on 2011-01-21
Ah ok, I was going on the official guide which states it needs at least 2GB of free space. In that case I will try another.

---

### Post by presence1960 on 2011-01-21
> **Qifor said:**
> Ah ok, I was going on the official guide which states it needs at least 2GB of free space. In that case I will try another.

I believe that is free hard disk space for the installation.

---

### Post by Qifor on 2011-01-21
No on the guide included on the download page as step 1 for creating a usb to install in windows it says "1. Insert a USB stick with at least 2GB of free space"

---

### Post by presence1960 on 2011-01-21
> **Qifor said:**
> No on the guide included on the download page as step 1 for creating a usb to install in windows it says "1. Insert a USB stick with at least 2GB of free space"

Well here is a screenshot of 10.04.1 on a 2 Gb flash disk. As you can see it only occupies 700 MB. So you should be fine with a 1 Gb disk.

---

### Post by Qifor on 2011-01-21
Dont worry I trusted you and was putting it on my 1GB as I typed that. Just explaining why I thought I could only use my 2GB one.

As it is this now works on my current computer but does not on the one im trying to install it on. On this one it comes up clearly in the bios by name and shows on the screen when trying to boot from it. On the other it isn't in the bios nor does it show on screen.

---

### Post by presence1960 on 2011-01-21
> **Qifor said:**
> Dont worry I trusted you and was putting it on my 1GB as I typed that. Just explaining why I thought I could only use my 2GB one.

As it is this now works on my current computer but does not on the one im trying to install it on. On this one it comes up clearly in the bios by name and shows on the screen when trying to boot from it. On the other it isn't in the bios nor does it show on screen.

Try all your usb ports including the ones on the front and see if it boots. Check your connections from usb to motherboard also. Make sure connectors are in place and seated properly.

---

### Post by Qifor on 2011-01-21
Still a no go.

USB ports are all working, checked with my mouse and keyboard but still wont boot from the usb.

---

### Post by ronnielsen1 on 2011-01-22
If I understand correctly, you can't get the flash drive install to work on any computer. If this is the case, did you try my suggestion from earlier?

> [http://www.pendrivelinux.com/boot-mu...multiboot-usb/]("http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/")

[http://www.pendrivelinux.com/multibo...sb-from-linux/]("http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/")

You could try one of these. I've always had them work

---

### Post by Qifor on 2011-01-22
It works perfectly fine on this computer, its just the one im trying to install it on that it wont work on. I also tried your suggestion and got the exact same result.

The other computer just doesn't detect/boot from it.

---

### Post by ronnielsen1 on 2011-01-22
The computer might have a problem booting from usb then. Try plop boot manager. It will boot from about anything.

[http://www.plop.at/en/bootmanager.html#download](http://www.plop.at/en/bootmanager.html#download)

---

