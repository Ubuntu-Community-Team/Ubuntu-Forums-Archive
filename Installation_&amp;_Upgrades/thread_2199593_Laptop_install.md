---
title: "Laptop install"
date: 2014-01-14
forum: Installation &amp; Upgrades
---

### Post by frog3764 on 2014-01-14
Greetings to the Group - I want to install Ubuntu 12.4 to my 10" laptop running XP.  Since the laptop has no cd drive, so what is the easiet way to get Ubuntu installed on it?  Can I copy the CD to the USB and install it that way from my regular pc?  All input is appreciated.

Jim

---

### Post by erhollowell on 2014-01-14
You can make your USB drive bootable and run from it. You might have to go into the bios and make usb drive higher on the boot priority if you do it this way. I have never done it this way but many do. Maybe they can fill you in on the details.

---

### Post by frog3764 on 2014-01-14
Hey ER - Do I need the USB bootable for XP or U?  I'm going to make the laptop running XP dual with U.  I would want to be able to run the U installer from the USB to get it on the laptop.  I don't want to run U from the USB, but only to get it installed.  Thanks for your input.

Jim

---

### Post by devine.steve on 2014-01-14
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

---

### Post by devine.steve on 2014-01-14
Also you need to shrink the partition so you have somewhere to install Ubuntu to. I suggest you make a good backup of your XP instance beforehand.
[https://help.ubuntu.com/community/HowtoResizeWindowsPartitions](https://help.ubuntu.com/community/HowtoResizeWindowsPartitions)  - Looks like you have to use GParted from within the Live USB instance.

---

### Post by Mark Phelps on 2014-01-15
It's been a while, but from what I remember, 12.04 does not fit on a CD, it's too big; instead, it has to be burned to a DVD.

Since you're running MS Windows, I would recommend that you check out PendriveLinux.com. I've used it often to create a bootable USB from Linux distro ISO image files.

---

### Post by frog3764 on 2014-01-17
Hey Group - thanks for your help, but nothing worked.  I'm trying to get U on my game pc with XP, and add it to my Asus laptop with XP.  I've used a couple of programs to make the flash bootable and loaded the U ISO but neither pc would boot from it even though I've changed the boot priority in the Bios screen.  So I'm stuck for now.

Jim

---

### Post by mörgæs on 2014-01-17
> **devine.steve said:**
> Also you need to shrink the partition so you have somewhere to install Ubuntu to. I suggest you make a good backup of your XP instance beforehand.
[https://help.ubuntu.com/community/HowtoResizeWindowsPartitions](https://help.ubuntu.com/community/HowtoResizeWindowsPartitions)  - Looks like you have to use GParted from within the Live USB instance.

Please don't. 
Windows itself should be used for defragging and shrinking Windows partitions.

---

### Post by frog3764 on 2014-01-17
I need to get the pc's to boot from the flash drive first.  The rest of the problems I'll deal with in time, but right now I can't get the boot right.  I also thought that U would create the right size partition for itself.

Jim

---

### Post by mikewhatever on 2014-01-17
> **mörgæs said:**
> Please don't. 
Windows itself should be used for defragging and shrinking Windows partitions.

Don't think XP can do the shrinking.

---

### Post by slooksterpsv on 2014-01-17
Make sure the drive is formatted as Fat32 as NTFS won't work. I use Unetbootin and download the desktop iso and have it take care of the rest.

---

