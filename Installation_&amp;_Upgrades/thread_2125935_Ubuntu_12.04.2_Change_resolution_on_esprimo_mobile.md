---
title: "Ubuntu 12.04.2 Change resolution on esprimo mobile v5535"
date: 2013-03-15
forum: Installation &amp; Upgrades
---

### Post by brs79 on 2013-03-15
Hello,

I have an Esprimo Mobile v5535 Laptop with the SIS 771/671 Graphics card.

In 10,04 i got this video card properly installed with the right drivers and video mode (1280x800) .

Now i followed the instructions from this site

[https://sites.google.com/site/easylinuxtipsproject/sis](https://sites.google.com/site/easylinuxtipsproject/sis)

After reboot they are not working for me i verified the files excist when copied over.

Then i tried to set it up with xrandr first by typing cvt 1280 800 60 
then add it with

xrandr --newmode "1280x800_60.00" 83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
xrandr: Failed to get size of gamma for output default

It fails sadly. 


Included snippet from my xorg log with sis related stuff.

Please some advise to get this going.

[    20.064] (II) LoadModule: "sis671"
[    20.082] (II) Loading /usr/lib/xorg/modules/drivers/sis671_drv.so
[    20.123] (II) Module sis671: vendor="X.Org Foundation"
[    20.123] (II) UnloadModule: "sis671"
[    20.123] (II) Unloading sis671
[    20.123] (EE) Failed to load module "sis671" (module requirement mismatch, 0)

---

### Post by MAFoElffen on 2013-03-15
So... But it still comes up on another fallback driver? And I see you are able to boot the kernel...

At the grub boot menu... if you go to the CLI, what does the output from "vbemode" say? Or from Linux CLI, the output from "xranr -q"?

Then:
```

lspci -vnn | grep -i VGA

```
...and copy over your /etc/X11/xorg.conf file over as a text file and attach to your post please?

---

### Post by brs79 on 2013-03-15
Her&#347; the out put from 

~$ xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       61.0* 
   800x600        61.0  
   640x480        60.0  


And here from

~$ lspci -vnn | grep -i VGA
01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter [1039:6351] (rev 10) (prog-if 00 [VGA controller]

and attached the xorg.conf

It is comming up in VESA.. i have a desktop everything boots fine except video is not working.

[ATTACH]240219[/ATTACH]

Attached the driver + xorg

---

### Post by MAFoElffen on 2013-03-15
Not meaning to offend, but you know I have to ask the obvious right?

There was a two tar files names meant for two different architecturals, 32bit or 64bit:
[https://sites.google.com/site/easylinuxtipsproject/file-closet/sis-32-bit-1204.tar.gz?attredirects=0](https://sites.google.com/site/easylinuxtipsproject/file-closet/sis-32-bit-1204.tar.gz?attredirects=0)
[https://sites.google.com/site/easylinuxtipsproject/file-closet/sis-64-bit-1204.tar.gz?attredirects=0](https://sites.google.com/site/easylinuxtipsproject/file-closet/sis-64-bit-1204.tar.gz?attredirects=0)

Inside each tar file, their file names  match, so unless there is a problem with the TAR itself when it was uploaded or downloaded... (Possible) then the other possibility is that you might be using the wrong architecture?

Are you running 32bit or 64bit? Did you get the right TAR file for that?

---

### Post by brs79 on 2013-03-16
Yea it is the correct file i have downloaded.
I followed the instructions from the site.

~$ arch
i686

Please not that it is a fresh install from Ubuntu 12.04.2 on the esprimo laptop v5535 nothing alterd or
 editted except the instructions from the site from the driver.

Could it be that the xorg.conf is not picked up ?

---

### Post by brs79 on 2013-03-16
Also here&#347; my log file for xorg: [ATTACH]240233[/ATTACH]

---

### Post by Pjotr123 on 2013-03-22
I am the author of the how-to at Easylinuxtipsproject. The cause of the problem probably lies in the new X.org that comes with 12.04.2 (it has not only the 3.5 kernel from Quantal, but also the X.org that goes with it). 
See: [https://lists.ubuntu.com/archives/ubuntu-devel/2012-August/035615.html](https://lists.ubuntu.com/archives/ubuntu-devel/2012-August/035615.html)

I have rewritten my how-to: use Xubuntu 12.04, Lubuntu 12.04 or Linux Mint 13 instead. They don't have the Quantal stack in their point releases, and won't get them in the updates either (Lubuntu and Mint don't have point releases at all, but Xubuntu does).

Regards, Pjotr.

---

### Post by tinmice on 2013-11-18
Hi, I've been trawling through old posts to try and sort the problem above, but have gotten nowhere so far.

It seems that I have the exact same output to brs79, but I have a clean install of Xubuntu 12.04. I followed the notes at the link below, but don't seem to be able to get it working, it still does not want to load the sis671 modules upon start and defaults to the standard sis module.

Any ideas? Sorry to dig up old threads, but I'm totally stumped now.

[https://sites.google.com/site/easylinuxtipsproject/sis](https://sites.google.com/site/easylinuxtipsproject/sis)

---

### Post by bellera on 2014-02-27
[https://sites.google.com/site/easylinuxtipsproject/sis](https://sites.google.com/site/easylinuxtipsproject/sis)

worked for me using 12.04.3 LTS 32 bit

However, xrandr doesn't show the two connectors of the card, LVDS1 and VGA1. So, VGA1 can't be controlled as I use to with other computers.

---

