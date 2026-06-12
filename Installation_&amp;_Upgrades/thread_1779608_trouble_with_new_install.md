---
title: "trouble with new install"
date: 2011-06-10
forum: Installation &amp; Upgrades
---

### Post by installman on 2011-06-10
Hi everyone hope you can help me
I just built a new computer specs are
i3 2100
 4 mb ram
biostar h67 motherboard
western digital sata hard drive
I have installed ubuntu 11.04 on my windows machine as a dual boot system with no problems, but when I try to install ubuntu on the new system it goes through the whole download and install procdure the says to restart. When I restart it takes forever to boot to the ubuntu screen then just stops. I can move the cursor around the screen with the mouse, but nothing else.I do not have windows on the new machine and don't want to go there please.
Thanks Stan

---

### Post by nzjethro on 2011-06-10
Can you boot live? That is, can you run Ubuntu from the LiveCD? If yes, do so, run Gparted, clean your entire disk, create a ext4 partition for Ubuntu (either the whole thing, or else the ext4 for Ubuntu and whatever other partitions you want) and try install Ubuntu on the clean disk. Starting from a nice clean disk will mean that Grub can set itself up nicely.

---

### Post by installman on 2011-06-10
I think I can still run from the flash drive. I will try your suggestion and reply shortly
Thanks Stan

---

### Post by installman on 2011-06-10
Ok I am now online with the try ubuntu selection off the flash drive. I can't seem to get access to do anything with the hdd. I tried to select install and it just locks up. Is it possible to download and install from the try ubuntu?
Thanks Stan

---

### Post by cmhorel on 2011-06-10
Is there a possibility there's something wrong with your hard drive? Recently I tried several times to install Ubuntu 10.04 and 11.04 on the same computer. Every time I tried to boot, the installation hung on the loading screen with the dots and just cycled forever. One of three of my hard drives was actually cooked, and when I removed it the installation worked perfectly.

---

### Post by installman on 2011-06-10
I guess its possible it is a new drive. how can i test it
Thanks Stan

---

### Post by wildmanne39 on 2011-06-10
> **installman said:**
> I guess its possible it is a new drive. how can i test it
Thanks StanHi, you can run a quick scan on the livecd by opening disk utilities.
It is probably a driver and hardware issue. You should try this guide and then post back.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by installman on 2011-06-11
nzjethro 
   I ran gparted created a new partition(the whole drive) and then installed ubuntu again. When I rebooted it booted ubuntu from the hdd and after login it seemed ok until I tried to eject the usb drive then it started flashing the window very fast and wouldn't let me do anything. I then re booted again and I got a message saying I didn't have the hardware required to run unity and told me to select classic from the boot menu then booted on its own into what I guess is classic(I have only used 11.04 for a little over a week and hadn't heard of ubuntu before then) on its own. Now for the next issue ubuntu doesn't see my dvd drive at all. I was going to run the drivers cd, but I can't get ubuntu to see the drive to install the drivers.

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **installman said:**
> nzjethro 
   I ran gparted created a new partition(the whole drive) and then installed ubuntu again. When I rebooted it booted ubuntu from the hdd and after login it seemed ok until I tried to eject the usb drive then it started flashing the window very fast and wouldn't let me do anything. I then re booted again and I got a message saying I didn't have the hardware required to run unity and told me to select classic from the boot menu then booted on its own into what I guess is classic(I have only used 11.04 for a little over a week and hadn't heard of ubuntu before then) on its own. Now for the next issue ubuntu doesn't see my dvd drive at all. I was going to run the drivers cd, but I can't get ubuntu to see the drive to install the drivers.

Does this happen with 10.10? Try this:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

---

### Post by installman on 2011-06-11
should I install the 32 bit version or the 64 bit version?
Thanks Stan

---

### Post by aarsalankhalid on 2011-06-11
> **installman said:**
> should I install the 32 bit version or the 64 bit version?
Thanks Stan
That depends on your system. But if you're not sure, just install the 32 bit version.

---

### Post by installman on 2011-06-12
-I have installed ubuntu 10.10 and it still doesn't see the dvd drive.
Thanks Stan

---

### Post by installman on 2011-06-12
spent some time searching,but no luck yet. The dvd drive is an asus x- multi

---

### Post by installman on 2011-06-12
It is working now. I had to change the sata settings in the bios to ahci and now everything seems to be fine. 
Thanks for your help
Stan

---

