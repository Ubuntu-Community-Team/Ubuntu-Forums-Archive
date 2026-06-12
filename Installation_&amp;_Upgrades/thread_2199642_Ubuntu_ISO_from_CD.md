---
title: "Ubuntu ISO from CD"
date: 2014-01-15
forum: Installation &amp; Upgrades
---

### Post by frog3764 on 2014-01-15
Greetings to the Group - I'm trying to get a copy of U 12.4 to a flash drive so I can install it to a laptop.  However, one of the options states I need an ISO.  So how can I get that from the original CD?  The only file I saw on the CD that looked like an ISO said ISOLinux and that folder was full of files.  I'm just trying to keep from having to download the ISO which takes up a lot of bandwidth on this temporarily slow ISP.  All input is appreciated.

Jim

---

### Post by carl4926 on 2014-01-15
Use Brasero or k3b to copy the CD and be sure to select create image only
The resulting .iso will be what you need

---

### Post by frog3764 on 2014-01-15
Hey Carl - YOU'RE THE MAN!  I'm off to do it.

Thanks,
Jim

---

### Post by frog3764 on 2014-01-15
Hey Carl - The Brasero program is already installed, but where do I go to select what the program wants?  The first window is the Image Burning Setup, then I need to select the image from the source CD. At the bottom I have to select what type of image, iso9600, auto, or readcd / readom image.  Then there is the list of the files on the CD.  I'm lost!

Jim

---

### Post by coffeecat on 2014-01-15
From the Brasero window: Disc Copy (Create 1:1 copy of a CD/DVD) -> In the Copy CD/DVD mini window, make sure the correct CD is selected in the upper drop-down. In the lower drop-down select Image File. Click the properties button and in the location window select your destination folder, adjust the filename if you wish and, most importantly, select ISO9660 from Disc Image Type.

---

### Post by carl4926 on 2014-01-15
It should look like this
[http://paste.opensuse.org/54420812](http://paste.opensuse.org/54420812)

---

### Post by varunendra on 2014-01-15
> **frog3764 said:**
> I'm trying to get a copy of U 12.4 to a flash drive so I can install it to a laptop.

Why don't you boot from the CD itself and use "Startup Disk Creator" program in the Live session to create the Live USB? It will use the CD itself as the source image, and is one of the most promising methods to make the flash drives Ubuntu Live bootable.

---

### Post by frog3764 on 2014-01-15
Hey  varunendra - Your suggestion sounded pretty good but as I was already stumbling through the Brasero program, I thought I would finsih working with it as I've needed an ISO before and always have trouble with that.

And Carl - I finally got the image.  The program seems a bit tough though as I had trouble with one of the little windows accpting my source CD.  Anyway, I finally got it so now I'll see if I can get that to install in my laptop from the flash.

Thanks for all the help.
Jim

---

### Post by varunendra on 2014-01-15
> **frog3764 said:**
> I've needed an ISO before and always have trouble with that.
...
...The program seems a bit tough though as I had trouble with one of the little windows accpting my source CD.

A much simpler, albiet slower way to create the iso from a CD/DVD is the dd command :
```
dd if=/dev/sr0 of=MyISOfile.iso
```
..where "/dev/sr0" is your CD inserted and detected by the system. It can be /dev/sr1,sr2 etc. in some cases, you can confirm which one it is by seeing the output of -
```
mount
```

"MyISOfile.iso" is the name of the target iso file. You can name it whatever you wish, the above is just an example. If you wish to put the image on your desktop, add "Desktop/" before the name (e.g. "of=Desktop/MyISOfile.iso").

I just created an ISO from a bootable DVD of Windows7 (about 4GB), finished at an average copy speed of 4 MB/s (expected, as it was copied to a nearly full NTFS partition). Booted a windows virtual machine from the iso - works perfectly.

**PS:**
General form of using dd command like this is -
```
dd if=*<input file>* of=*<output file>*
```
The "if=" stands for "Input File=", while "of=" means "Output File=".

When copying a disk to image, the "if=" is the device file that represents the device (not its mount point), and the "of=" is the image file that is to be created.
When copying (cloning) directly from a device (e.g. CD) to another device (e.g. a USB flash disk), "if=" is the device file representing the CD (e.g. /dev/sr0) and "of=" is the device file representing the flash drive (e.g. /dev/sdb).

[COLOR="#FF0000"]**CAUTION !** Be very careful while using dd in the above manner ! If you reversed the "if=" and "of=" arguments and used a writable diskfile address with "of=", you may end up totally destroying the existing data on that disk.[/COLOR]

---

### Post by Topsiho on 2014-01-15
"I'm trying to get a copy of U 12.4 to a flash drive so I can install it to a laptop. However, one of the options states I need an ISO. So how can I get that from the original CD?"

This sentence is a mystery to me. You state that you have a copy ("original CD") of U 12.04, and that you need an .iso file. Well, if you downloaded U 12.04 from Ubuntu, this copy already IS an .iso file. It's extension is .iso. (*Or it is made from the .iso file, and should already be usable, though I doubt that a CD has enough capacity*). It is what is called an image of Ubuntu 12.04.

You can use it straight as it is to burn a DVD-rom using brasero (starting brasero, using "burn as an image" or something like that (the lowest button, I have a Dutch translation).
Or you can make a bootable USB-stick (> 2GB) using Startup Disk Creator, if that is the English name.

You have to take care you have downloaded the correct .iso file: for 32 bits, or 64 bits.

Topsiho

---

### Post by Topsiho on 2014-01-15
I have been thinking again. You have a CD but you need a USB-stick, which you want to create from the CD? Then the easiest thing to do is go to the Ubuntu site and just download the correct and latest .iso file for Ubuntu 12.04. I just hope that your internet connection is fast, but even if it takes hours, you have your .iso file, with a minimum of updates (even if it is quite a number now, and might take some time again) to install after the install.
And always check the USB-stick (or live CD or DVD) before you install.

Topsiho

---

