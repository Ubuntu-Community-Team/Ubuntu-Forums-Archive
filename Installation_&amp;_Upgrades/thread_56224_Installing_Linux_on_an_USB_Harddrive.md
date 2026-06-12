---
title: "Installing Linux on an USB Harddrive"
date: 2005-08-11
forum: Installation &amp; Upgrades
---

### Post by Trexx on 2005-08-11
Hello.

I'm thinking about installing Ubuntu on my external harddrive. 
It's an 80gb USB2.0 harddrive, and I need information.

Is it possible to partition my external harddrive so I can have 20gb for Linux and the remaining 60gb for my backup files? I know it's in FAT32 format, and I want to know if it's possible before I back all my other stuff on my main NTFS harddrive to partition it.

Thanks for your help!

EDIT:
I am extremely sorry, but I meant this to go in the 4.10 version forum, I accidentally put it in here. Sorry!

---

### Post by Copter on 2005-08-12
hi!

i did it on hoary 5.04 using [this](http://www.ubuntuforums.org/showthread.php?t=20522) method. its from warty 4.10 actually but works also in hoary 5.04.

i did it on 40gb hdd drive. be sure that your motherboard / bios lets you boot form usb devices. some board doesnt support this. i have formated this drive (deleted everything on it) and partitioned it like this:

swap swap 1gb (never used more than 200mb of it, i have 512mb of ram)
/ (root) ext3 9gb
/home ext3 5gb
/fat32space 25gb

this way i can boot form it home and use it also as portable usb hdd (25gb fat32 space with movies and music accessed from any system)

good luck!

copter :]

---

