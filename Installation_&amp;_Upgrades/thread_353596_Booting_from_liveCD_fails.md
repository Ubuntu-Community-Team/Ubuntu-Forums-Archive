---
title: "Booting from liveCD fails"
date: 2007-02-04
forum: Installation &amp; Upgrades
---

### Post by eapache on 2007-02-04
I downloaded and burned a cd of ubuntu 6.10. It works fine on all the other computers I've tried it on, however, on my old Dell Optiplex GX150, I'm having trouble getting the liveCD to display properly. I am using a PCI ATI Radeon 7200 graphics card (yes, I know it's old), which works fine on XP. When I choose to boot from cd in my BIOS, I get the normal liveCD menu. The memory test works fine, but no matter what graphics setting I use,  booting Ubuntu doesn't work. I've tried all the settings, in regular and 'safe graphics mode'. No matter what I use, I get the boot splash screen, and then a blank screen. Nothing else happens. If I unplug my monitor from the Radeon and into the onboard graphics port, I get a whole bunch of garbage (in the form of randomly coloured vertical lines). I've tried  ctrl-alt-F1 and ctrl-alt-dlt to no avail. At this point it seems to be frozen. However, if I set my default graphics in my BIOS to be the onboard card, and use that, it boots fine. I'd really like to get this working, but I don't understand the problem. I thought that 'safe graphics mode' was supposed to be indestructible, so I'm wondering if it's a BIOS setting or something. It works fine on Windows though...

Does anybody have any ideas on what I could do to try and fix this?

---

### Post by p!=f on 2007-02-04
Try to boot without "vga=" and "splash" kernel options or download and use alternate CD install.

---

### Post by amohanty on 2007-02-04
Have you tried waiting :)

I have one of those too and it can take upto 12-20 minutes for X to load up..

AM

---

### Post by aberry5555 on 2007-02-05
This is a big old problem with ATI graphics on the Ubuntu install, though I didn't think it went as far back as that card :p basically the driver called "ATI" that Ubuntu defaults to doesn't usually work by itself, even though other distros do it out the box. It is, though, fairly easy to get working again.

On the first boot screen (the one giving you boot options) press F6 to edit the boot options line. 

Delete "quiet - splash" and type in "break=bottom". This will rid of the fancy looking ubuntu loading bar and give you a command line half way through booting. 

When you get the command line type "chroot /root nano etc/X11/xorg.conf". This will bring up your xorg.conf file, which is the file that Ubuntu uses to set up your graphics. Scroll down the page until you see a heading called "Device". 

There should be a sub-heading under this called "Driver" with the driver listed to the right. This will probably be "ATI" (the faulty driver), now change it to "radeon" (this driver should work but, if it doesn't, repeat the steps and use the driver "vesa" instead, which gives the most basic graphics: like windows safe mode only a bit better :p). 

Once you've changed it press "ctrl+O" then "ctrl+X", this will bring you back to the command line. Unless you want to do anything else type in "exit", this should load up the rest of Ubuntu and, fingers crossed, your Graphics will work :)

I really hope they fix this bug soon as I've posted the work-around about ten times now, and that's after I've found it myself in the forum!

---

### Post by DutchCook on 2007-02-05
Hi, I get the message: "/bin/sh: can't acces tty; job control turned off
and then I have a command line (initramfs).
I'm another Linux beginner, but I want to learn a lot :) 
I have an Asus laptop, A6Va with a ATI X700, I think my problem is related to the topic starter his.

---

### Post by eapache on 2007-02-05
Thanks aberry5555, hopefully your solution will work. Only one question: if it does work, how do I get it to install on my hd with that option, not the default?

---

### Post by eapache on 2007-02-05
OK... the only visible device was my intel built-in, so I changed that to radeon, and then vesa. Both times I got an x server crash, and an error something like this:

Screens detected, but none have correct configuration. No device detected at PCI 1:8:0

So just for the heck of it, I booted again, and as well as changing the driver from Intel386 (or something similar) to radeon, I also changed the PCI address from 2:0:0 to 1:8:0. It worked. I am typing this from the liveCD.

Apparently, it was configuring the intel builtin wrong, and not even detecting the radeon. When BIOS told x that PCI 1:8:0 was the default graphics. it was crashing because it thought there was nothing there... does this make sense to anyone with more linux experience?

---

### Post by eapache on 2007-02-05
I tried install, and it hung at 65%. I can now consistently get the CD to boot, so that problem, however, is solved. Hopefully the problem with the installer was a one-time issue, so I'll try again when I have time. Thanks for everyones' help.

---

### Post by aberry5555 on 2007-02-06
It wasn't crashing because there was nothing there, it was crashing because intel graphics chipsets need a special driver, and won't work with the bog-standard vesa driver unfortunately. you could, however, set it up with the intel drivers now and have a second output, if you wanted it for some reason :p

Dutchcook try what I said and also, if you have a secondary built in chipset, do as eapache said. Good luck!

---

### Post by Platinum89 on 2007-02-19
> **aberry5555 said:**
> 
On the first boot screen (the one giving you boot options) press F6 to edit the boot options line. 

Delete "quiet - splash" and type in "break=bottom". This will rid of the fancy looking ubuntu loading bar and give you a command line half way through booting.  I tried this, but it didn't give me a command line.

> 
When you get the command line type "chroot /root nano etc/X11/xorg.conf". This will bring up your xorg.conf file, which is the file that Ubuntu uses to set up your graphics. Scroll down the page until you see a heading called "Device".  

Couldn't try this or the balance of your suggestion without the command line coming up. I'm using Ubuntu 5.10 (I tried all flavors of 6.06 , the latest and they all failed on this box). The box uses a ATI Radeon 7000 w/32MB. I have an onboard Intel graphics chipset, but it really sucks compared to the ATI. I'd like to keep the ATI if at all possible. Any ideas how I can utilize your suggestion for 5.10??? :confused: 

Regards and thanks in advance!

---

### Post by jkeyes0 on 2007-02-23
> **aberry5555 said:**
> This is a big old problem with ATI graphics on the Ubuntu install, though I didn't think it went as far back as that card :p basically the driver called "ATI" that Ubuntu defaults to doesn't usually work by itself, even though other distros do it out the box. It is, though, fairly easy to get working again.

On the first boot screen (the one giving you boot options) press F6 to edit the boot options line. 

Delete "quiet - splash" and type in "break=bottom". This will rid of the fancy looking ubuntu loading bar and give you a command line half way through booting. 

When you get the command line type "chroot /root nano etc/X11/xorg.conf". This will bring up your xorg.conf file, which is the file that Ubuntu uses to set up your graphics. Scroll down the page until you see a heading called "Device". 

There should be a sub-heading under this called "Driver" with the driver listed to the right. This will probably be "ATI" (the faulty driver), now change it to "radeon" (this driver should work but, if it doesn't, repeat the steps and use the driver "vesa" instead, which gives the most basic graphics: like windows safe mode only a bit better :p). 

Once you've changed it press "ctrl+O" then "ctrl+X", this will bring you back to the command line. Unless you want to do anything else type in "exit", this should load up the rest of Ubuntu and, fingers crossed, your Graphics will work :)

I really hope they fix this bug soon as I've posted the work-around about ten times now, and that's after I've found it myself in the forum!

Thanks very much for this. I had no problem installing on my laptop, but when I used the same CD for my desktop, it locked up on startup with no video. Editing the xorg.conf file got me in (using the vesa driver) and I'm installing now. Sadly, there's something funny about the way my SATA drives are recognized and it doesn't want to let me install there, so I'm having to install to my IDE drive (2 SATA drives and 1 IDE). Eh well. I'll just use the SATA for storage.

Thanks again!

---

### Post by waterfoul on 2007-02-26
> **DutchCook said:**
> Hi, I get the message: "/bin/sh: can't acces tty; job control turned off
and then I have a command line (initramfs).
I'm another Linux beginner, but I want to learn a lot :) 
I have an Asus laptop, A6Va with a ATI X700, I think my problem is related to the topic starter his.

I'm having this same problem.  (I am also a serious n00b here; it's literally my first attempt at Ubuntu tonight.)

Pressing F6 on the first boot screen brings up a line that ends in "quiet splash --", *not* "quiet - splash."  I tried deleting the "quiet splash" (and left the "--"), replacing it with "break=bottom" as directed, and then ended up where DutchCook was:  the "initramfs" command line.  I tried typing "chroot /root nano etc/x11/xorg.conf" at this point, and it brought me to a screen that said it was a new file.  It certainly didn't bring up xorg.conf.

I'm confused.  Any help would be appreciated.  6.10, trying to boot from CD, ATI Radeon 7000.  Thanks!

---

### Post by navy78 on 2007-03-16
> **waterfoul said:**
> I'm having this same problem.  (I am also a serious n00b here; it's literally my first attempt at Ubuntu tonight.)

Pressing F6 on the first boot screen brings up a line that ends in "quiet splash --", *not* "quiet - splash."  I tried deleting the "quiet splash" (and left the "--"), replacing it with "break=bottom" as directed, and then ended up where DutchCook was:  the "initramfs" command line.  I tried typing "chroot /root nano etc/x11/xorg.conf" at this point, and it brought me to a screen that said it was a new file.  It certainly didn't bring up xorg.conf.

I'm confused.  Any help would be appreciated.  6.10, trying to boot from CD, ATI Radeon 7000.  Thanks!


I have the same problem, I try to start the live Ubuntu,but my screen become black after 20 minutes of waiting... 
I try the same things tried by waterfoul, but nothing to do! Please help me!!!

I have a notebook:
asus a6va q21h 
ati radeon x700 128 mb ram
Intel Pentium M processor 740
1 GB di ram

---

