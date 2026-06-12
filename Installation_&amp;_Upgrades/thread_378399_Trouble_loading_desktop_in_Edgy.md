---
title: "Trouble loading desktop in Edgy"
date: 2007-03-07
forum: Installation &amp; Upgrades
---

### Post by tminter on 2007-03-07
Hi,

I have recently tried to install Ubuntu 6.10 edgy onto my desktop.  I had to use the alternate disc image to get the installer to work properly.  Now i have it installed and I can get to the login screen.  Here i can log in but the next screen is [this one]("http://i27.photobucket.com/albums/c174/tminter51/P3070003.jpg")

I would guess that I have to install the correct display drivers but I don't know how I can access the USB stick that they are on.

Any help would be appriciated.

Spec:

E6600
Asus P5N32-E SLI
2*1Gb Geil DDR800
BFG 7800GT

---

### Post by ArieT on 2007-03-07
You can acces your usb-disk from the commandline. You can open a console by pressing ctrl+alt+F1-6 . Are you sure the usb stick contains Linux drivers?

---

### Post by tminter on 2007-03-07
Yes there are linux drivers on there that I have downloaded from the Nvidia site.  When I try to access the USB disk using "cd /media/usb" it replies "no such device or directory"

---

### Post by zvacet on 2007-03-08
> To Mount Media

To mount media is to make the file
system of the media available for access. When you mount media, the file system
of the media is attached as a subdirectory to your file system.

To mount media, insert the media in the appropriate device. An object
that represents the media is added to the desktop. The object is added only
if your system is configured to mount the device automatically when media
is detected. 

If your system is not configured to mount the device automatically,
you must mount the device manually. Double-click on the Computer icon from the desktop. A Computer  dialog
is displayed. Double-click on the object that represents the media. For example,
to mount a floppy diskette, double-click on the Floppy
object. An object that represents the media is added to the desktop.
I hope this help.

---

### Post by tminter on 2007-03-08
Cheers, tho I am unable to get into the desktop :(

I have managed to get the cd mounted in teh command line using

sudo mount cdrom0

when in the /media/ directory.


The problem I have atm is that I can't insatll teh NVIDIA drivers. when i try to get them to install I get the following message:

 ./nvidia-installer : 2 : syntax error : ")" unexpected

Any help would be good.

---

### Post by tminter on 2007-03-08
Problem resolved.  It turns out i was using the IA64 drivers rather than the EMT64 drivers

---

