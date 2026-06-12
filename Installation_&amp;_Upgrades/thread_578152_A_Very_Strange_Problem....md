---
title: "A Very Strange Problem..."
date: 2007-10-16
forum: Installation &amp; Upgrades
---

### Post by typesour on 2007-10-16
Okay, so a few days ago I tried to upgrade feisty on ubuntu. It was all fine and dandy until I restarted my computer...I got GRUB error 18. So I booted from the install CD and went about trying to repartition my drives and/or restore GRUB. I followed the instructions for installing GRUB, but it wouldn't work. This is the terminal output:

```

grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found


```

I KNOW the file exists, it's sitting on my desktop under "disk-1". What do I do? And is there any way to just backup my HD (disk-1) to a portable hard drive or something and reinstall using gutsy? Right now it only opens files as read-only and I can't copy them to an external. I don't even care about my settings, I just want to save my documents and start again! Augh.

Any help is MUCH appreciated.

---

### Post by gsiliceo on 2007-10-17
Try changing hd0,0, to hd1,0, because grubs has a strange way of numering your hard disks different that gparted or the linux kernel itself.

Or if you can, change the order of your hard disks in your bios.

Meanwhile you can download and burn the Super Grub cd, it has wizards to boot your system, and it can probably fix it, but i dont recommend trying it.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

If the file exists as you say, you will find it using SUper Grub, and your linux will boot because it will bot.

---

### Post by typesour on 2007-10-17
Thanks for your help! Unfortunately, I can't try the second option because my comp will only run from the ubuntu install  CD, so I can't take it out. I tried changing hd0 to hd1, and that got me through the process the how to explained earlier, but when I restarted my computer I got the same grub error 18. 

Although, as if by magic, I can now access some of the files from my hard drive. I've copied them to a thumb drive and I think I'll try reinstalling ubuntu. But I'd like to get my media files as well, all my music and pictures. Right now, my computer tells me that I don't have permission to access that folder, or change any of its settings. Is there any way to use the install cd to, I don't know, pretend I'm my root user and give permission to change those files? 

Thanks for your help!!

---

### Post by forestpixie on 2007-10-17
try running nautilus as root

```
gksudo nautilus
```

---

