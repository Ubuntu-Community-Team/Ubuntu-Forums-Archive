---
title: "normal install and persistent usb"
date: 2011-11-22
forum: Installation &amp; Upgrades
---

### Post by pixiq on 2011-11-22
Hi, this is my first question

What is the difference between normal install and persistent USB. If I want to install Ubuntu to a USB drive, what should I select and why?

---

### Post by WasMeHere on 2011-11-22
Welcome to the Ubuntu Forums, pixiq,

You can find several thread about this topic in the Ubuntu Forums.
Search for ***persistent usb boot***

Have fun finding out :-)
Olle

---

### Post by pixiq on 2011-11-22
Maybe I have to ask more details -- If I want to install Ubuntu to a USB drive, what should I select and why?

I have seen that people make USB boot drives with Ubuntu's method, Unetbootin and Multisystem
[http://ubuntuforums.org/showpost.php?p=11458343&postcount=43](http://ubuntuforums.org/showpost.php?p=11458343&postcount=43)

Why not a normal install to the USB drive? How is flash drive different from hard disk? What do you suggest?

---

### Post by WasMeHere on 2011-11-22
A USB boot drive is similar to a CD boot drive. You can run a live system to test how it co-operates with the hardware of your computer. And then install it to your hard drive, if it looks good.

The persistent usb takes advantage of the fact that read/write is possible on a USB drive, so in addition to the live system, you have also a file-system where you can store changes to the system and personal files. But still, this is a system that should run on most computers, it is not set to fit a particular computer, but is portable.

Flash drives are less sensitive to mechanical shock and wear, but cannot be written/re-written as many times as a conventional hard disk with a magnetic layer to store the data. Regular installation to disk creates more writing, so hard disks are better for that. Furthermore, I think that USB connections are slower than the internal IDE (PATA) or SATA connection (at least USB 2.0).

[COLOR="Red"]Anyone reading this post, please help me describe this if you know more than I[/COLOR] about the difference between hard drives and flash drives and what to suggest!

---

### Post by pixiq on 2011-11-22
Thank you for the explanation, Olle :)

Can someone help me to select what to install: what version of Ubuntu is easiest to get running? And should I install it or run it as persistent USB?

---

### Post by gordintoronto on 2011-11-22
It might help of you told us a bit about your computer: laptop or desktop, CPU, memory, hard drive, video adapter.

My personal preference is the latest version of Desktop Ubuntu, 64-bit on computers which support it. But run it from a flash drive or CD first, to make sure it works with your hardware.

---

### Post by sudodus on 2011-11-22
> **pixiq said:**
> Thank you for the explanation, Olle :)

Can someone help me to select what to install: what version of Ubuntu is easiest to get running? And should I install it or run it as persistent USB?
The default or 'vanilla' Ubuntu should be easy, otherwise it wouldn't be default, right? And you should have the new version otherwise you don't get support for new hardware. Unless you have an old computer, then the long time support (LTS) version is best, Ubuntu 10.04.

Take care to read the sticky posts on the Ubuntu Forums, they helped me quite a lot! But I have to admit that I got help from some colleagues at work to take the first linux steps.

---

### Post by pixiq on 2011-11-22
> **gordintoronto said:**
> It might help of you told us a bit about your computer: laptop or desktop, CPU, memory, hard drive, video adapter.

My personal preference is the latest version of Desktop Ubuntu, 64-bit on computers which support it. But run it from a flash drive or CD first, to make sure it works with your hardware. Good idea :D
desktop
amd athlon 64 x2 4400+
2 GB RAM
nvidia grapic chip
wired internet
320 GB hard drive

laptop
ibm thinkpad t41
1 GB RAM
64? MB graphic chip (from memory)
wired and wireless LAN
small hard drive (60 GB?)

---

### Post by sudodus on 2011-11-22
> **pixiq said:**
> Good idea :D
desktop
amd athlon 64 x2 4400+
2 GB RAM
nvidia grapic chip
wired internet
320 GB hard drive
I think vanilla Ubuntu will work on the desktop, whatever version you want 10.04 - 11.10
> laptop
ibm thinkpad t41
1 GB RAM
64? MB graphic chip (from memory)
wired and wirelan LAN
small hard drive (60 GB?)Maybe vanilla Ubuntu 10.04 will work on your laptop. Maybe try a newer version and a light desktop, Xubuntu or Lubuntu. The hard drive is small. Do you intend to keep the original OS (Windows I presume)? Is this why you ask about persistent USB?

---

### Post by pixiq on 2011-11-22
Windows XP on the laptop. Not too much software and files. Would it be enough with 12 GB for Ubuntu? Or should I run from USB?

---

### Post by gordintoronto on 2011-11-22
You can try Ubuntu with 12 GB. For me, it wouldn't be enough space for my music, and then I have hundreds of GB of videos.

---

### Post by sudodus on 2011-11-22
> **pixiq said:**
> Windows XP on the laptop. Not too much software and files. Would it be enough with 12 GB for Ubuntu? Or should I run from USB?
You can try both. 12 GB should be enough. 

First defrag XP. Then edit the partitions. Do you know of gparted? When you run a live session, use gparted to first shrink your windows partition, then make an ext3 or ext4 partition for ubuntu and a 1 GB partition swapping. After that you can install Ubuntu.

---

### Post by pixiq on 2011-11-22
Thanks guys, I'll go ahead and try :-)

---

### Post by pixiq on 2011-11-23
Hello everybody

I read that the LTS version is good for old computers and that it is very stable (recommended for companies). Both computers run well with Ubuntu 10.04 Lucid Lynx 32-bit (i686). Even the WLAN works. It looks the same when I run the desktop with Ubuntu 10.04 Lucid Lynx 64-bit (amd). What is the difference?

I might try also the new version, but unless it is much better I'll stick with Ubuntu 10.04. (Only testing live from CD so far)

Thanks a lot :KS

---

