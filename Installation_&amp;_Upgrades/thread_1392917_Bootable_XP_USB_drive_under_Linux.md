---
title: "Bootable XP USB drive under Linux"
date: 2010-01-28
forum: Installation &amp; Upgrades
---

### Post by nzso on 2010-01-28
After doing some research I have not found an answer to my question so I thought I would lay it on you guys. I am thinking of doing a dual boot of XP and Ubuntu. I have Ubuntu 9.10 installed now. The system it is installed on is a netbook. Ubuntu was installed on the netbook using a bootable usb drive I created simply because I have no external CD/DVD drive.

My problem is I need to create a bootable XP usb drive and I can't seem to locate any program or tutorial on how to do this under linux. Is there a program for Ubuntu that will make a bootable install on a usb drive similar to the programs like WinToFlash and BartPE for Windows?

I still have my bootable usb drive for linux but without one for XP I am kinda stuck without wasting money on an external CD/DVD drive just for this purpose.

Thanks in advance! ;)

---

### Post by Leppie on 2010-01-28
i'm not sure how to do this, but i'll give it a shot.
create a bootable image with bartpe, then in ubuntu transfer the iso to the usb stick using the dd command. it's something like this:
```
sudo dd if=/path/to/windowsimage.iso of=/path/to/pendrive
```

---

### Post by nzso on 2010-01-28
So Bartpe will work under Ubuntu? Or you running it under wine?

---

### Post by Leppie on 2010-01-28
> **nzso said:**
> So Bartpe will work under Ubuntu? Or you running it under wine?
sorry, i've misunderstood.
you don't have access to a pc with an installed os and cdrom at all?

---

### Post by nzso on 2010-01-29
No, I am on the road and the netbook is the only pc I have with me.

---

### Post by Leppie on 2010-01-29
> **nzso said:**
> No, I am on the road and the netbook is the only pc I have with me.
you could try bartpe through wine, or otherwise install windows in virtualbox

---

### Post by tarsius4 on 2010-01-30
I'd like to learn how to do this as well.  I pretty much use Linux full-time, but now I have a crashed netbook with Ubuntu installed from XP SP3 via Wubi.  I can no longer boot Windows or Linux and I'd like to try using a Windows Recovery Disc to scan the drive before I resort to wiping the whole thing.

The problem is: How does one USE Ubuntu to make a bootable usb drive from a WINDOWS iso file.

There's plenty of info regarding using Windows to create bootable Windows drives, Windows to create Linux drives, and Linux to create Linux drives. But where can I find instructions for using Linux to create a bootable Windows USB drive from a Windows Recovery CD ISO (note: a .iso file, not .img file)

Thanks

---

### Post by nzso on 2010-02-04
Bump

---

### Post by Leppie on 2010-02-04
> **nzso said:**
> Bump
bump what?

---

### Post by nzso on 2010-02-04
Bump the thread to see if anyone else has an alternative solution.

---

### Post by Leppie on 2010-02-04
i still don't understand if you already have a bootable windows image (like iso or img file). if you do, you can use usb-imagewriter to transfer to a usb stick. imagewriter only accepts .img files, but you can just rename a .iso to .img without any problems.

---

### Post by nzso on 2010-02-04
Yes, I have a .iso file of WinXP and was not aware that you could use "usb-imagewriter" to create a bootable usb drive and have windows install correctly. I assumed that there would be issues during the reboot points of the installation since as I understood it "usb-imagewriter" was not meant to create Windows XP bootable drives?

---

### Post by Leppie on 2010-02-04
> **nzso said:**
> Yes, I have a .iso file of WinXP and was not aware that you could use "usb-imagewriter" to create a bootable usb drive and have windows install correctly. I assumed that there would be issues during the reboot points of the installation since as I understood it "usb-imagewriter" was not meant to create Windows XP bootable drives?
i'm not sure it's all that different. most systems emulate a floppy disk when booting off cd to provide compatibility with older systems. i have never tried to create a bootable win usb though.
but i guess it would be worth trying?

---

### Post by nzso on 2010-02-04
Unless it's been confirmed to work I don't feel like it would be worth the hassle. I know when I had used wintoflash to install windows off of a usb drive at one point there were methods used to catch the installation again after the reboot process of the installation so I am not sure how that would work with your method. It's a shame someone hasn't programmed a tool that I know of to quickly accomplish this task.

---

### Post by Leppie on 2010-02-04
well, good luck with it then.

---

