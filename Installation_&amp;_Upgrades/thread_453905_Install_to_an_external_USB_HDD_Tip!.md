---
title: "Install to an external USB HDD Tip!"
date: 2007-05-24
forum: Installation &amp; Upgrades
---

### Post by onaclov2000 on 2007-05-24
I am at work at the moment so I will try to give the best description of my tip and I will update it as needed.

Here is my setup,

HDD: I have an Internal USB drive with a IDE to USB cable that enables me to use it as a USB device.  I have 5 total partitions on it, 3 Fat32/NTFS partitions, and a swap partition and a ext3 partition now.  

Comp: Dell Laptop with the defaulted partitions.

Goal: I planned to install Ubuntu on my External HDD mentioned above.  

Install from Live CD

After many and much problems, I was using the live installer, when I got to the screen that I could choose where the GRUB would be installed, (last screen before starting install), I found that if I left it default, it would overwrite my MBR on my Laptop. 
Then of course I was unable to enter windows, and my grub had some Error 22 or 23 (I believe), so things appeared to be hosed here.  I did a fix MBR from my laptop and got things started over from scratch again.

I went searching,
From what I was looking at in my Grub Boot Folder it was saying that:

hd0 = /dev/sdb0  (my laptop) (default)
hd1 = /dev/sdb1 (my external HDD)

This was why my MBR was being overwritten.

In order to place it on the external HDD, I set it to hd1.

This enabled me to get GRUB to show up everytime, but I was still saying that my partitions couldn't be found.

This is where I learned something.
When you have the HDD connected and you boot via the live CD,

hd0 = (LAPTOP HDD)
hd1 = (EXTERNAL HDD)

GRUB on my External HDD that is now showing up NOW thinks this:

hd0 = (EXTERNAL HDD)
hd1 = (LAPTOP HDD)

From here there are 2 options I know of

1. At the GRUB menu, I did an edit and "temporarily" edited my location to look for my partition, and was    
    able to temporarily get the drive to boot.

2. Use the Live CD to get back into a linux environment and be able to access your External HDD

From here you need to edit (I believe this is the name of the file) menu.lst, and change your boot partition for Ubuntu from hd1, to hd0,(partition #).  Making your GRUB look at the right drive.  

What happens is this when the LIVE CD is used:
     Computer Boots, Linux loads and your computer where the C:\ resides is the primary drive (hd0), and 
     the External HDD is more secondary (hd1).

What happens is this when the computer boots FROM USB:
     Computer Boots, GRUB sees the External HDD as PRIMARY now (hd0), and the Laptop HDD as    
     SECONDARY (hd1), which is why we need to update our Menu.lst file.

Any Questions please let me know.

Thanks
onaclov

ATTN: MODS, if this is worthy of adding or sticking on to any other FAQ's, TIPS, ETC, please do so

---

