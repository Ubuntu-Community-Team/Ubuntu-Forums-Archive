---
title: "Success: 8.04 to 8.10 using 4GB Flash"
date: 2008-11-04
forum: Installation &amp; Upgrades
---

### Post by speed32219 on 2008-11-04
This is a feel good post, I know that some are having issues, but wanted to share a good install.

I wanted to try intrepid prior to removing hardy (Since I have it working great now), so I followed some threads here about setting up 8.10 on a 4GB flash.  I am here to say that I will from now on only use this method prior to installing and testing new releases.

I have successfully created a fully functional intrepid release on 4GB of flash.  I am amazed that I have my HTPC fully operational as well as the Trendnet 424UB (56Mbps usb wireless) and Turtle Beach sound card using spidf optical running 8.10.

Why am I amazed, well it took quite a while with hardy to get everything working, new drivers, modified scripts and SW patches to get everything working.  With Intrepid the only thing I needed to add manually was Envyng for support of my Evga Geforce 6200 AGP 8X video card with the 177.xx driver. (Prior driver using Hardy was 174.xx)

I would not have even tried Intrepid, since Hardy is working great for me now, but upgrading HW to the new Intel G45 chip set with Integrated HD (X4500) video and wanted a base system for testing.  I now have a working Intrepid release on Flash and now I can start my new HW project.

I am typing this not on my HTPC (I do not want to fire up my projector) but in my hone office where I put the newly created flash in a USB port and booted from it.  To my amazement, it fully loaded (recognized new Intel chipset ICH5, video, etc) and the only error was that my graphic display changed (From the default Nvidia to ATI) and went into low graphics mode, which is perfect on my 15" LCD 1024X768 display. I even plugged in the Trendnet wireless usb adapter and unplugged the Ethernet cable for testing and wireless came up and took over the connection.

I am a happy camper. :guitar:  Rock on Ubuntu.

Now moving on to my new HW project and reviewing posts of the new Intel chipset, seems as if all the bugs are worked out with the latest updates for an Intel DG45ID MB.  Thank you Beta testers. :popcorn: 

Thanks to all who provided guidance to complete a fresh install of  Intrepid to a 4GB flash card.

---

### Post by n6yga on 2008-11-04
It's good to hear a happy post about upgrade/install for a change!


Mark.

---

### Post by richlyn9 on 2008-11-04
It the flash install a persistent one?
how did you go about it?as i want to make a casper persistent 8.10 install on a 4gb pendrive(do i need more space?)
I have downloaded the .iso file to my desktop.

---

### Post by C.S.Cameron on 2008-11-04
Have tried dozens of times using usb-creator to install to a 4 gig Kingston, without success.

This is what has worked for me so far:
Booted Live CD.
Plugged in flash drive.
Started Partition Editor
Created 1 GB FAT32 partition, (on the left side of the bar).
Created a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw".
Created a partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started usb-creator.
Selected minimum Stored in reserved extra space, (128 MB).
Pressed "Make Startup Disk.
When usb-creator finished, ran "gksu nautilus"
Selected disk and deleted casper-rw.
Shutdown, removed CD, rebooted.
Changed desktop background, connected to wireless and installed FontForge, created new user with password..
Rebooted, all changes were persistent.
Now I can upgrade the kernel without loosing my settings and installed applications.

---

### Post by speed32219 on 2008-11-05
I didn't use USB creator.  I disconnected my HD's power, put usb flash in, loaded 8.10 beta (Had for 2 weeks)CD ISO and did a fresh install right to the USB stick.  Formatted in EXT3, used guided, whole disk in Gparted from live CD and let it rip.

Downloaded updates and rebooted using usb.  Then shutdown and connected HD's. Copied my old /etc/fstab over and created mount points in /media.  Then did sudo apt-get install envyng-gtk from terminal.  Copied over a saved copy of .asoundrc, enabled iec958 output in alsa and that's about it.

---

