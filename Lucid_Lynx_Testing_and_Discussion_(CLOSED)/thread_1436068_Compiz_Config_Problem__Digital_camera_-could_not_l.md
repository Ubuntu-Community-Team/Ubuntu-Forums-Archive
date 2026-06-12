---
title: "Compiz Config Problem / Digital camera -could not lock device"
date: 2010-03-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by BrokeMahPC on 2010-03-22
Was testing Licid Beta 1 i386 desktop and everything works great apart from 2 issues:
1-Compiz config
When I select 4 desktops under General options to get the cube shape - it flicks back to 2 desktops after 1 second all on it's own.
-I have selected visual effects -extra
-It allows me to rotate the 2 desktops
-I have an ATI Radeon HD 4670
-After install I was not prompted to install a video driver as in past versions.
-An open source ATI driver is installed but does not appear under System - Admin - Hardware Drivers
- have a feeling I may need to reinstall this driver but can't remember how?

2- The digital Camera conflict between Gnome gvfs and F-Spot resulting in the "could not lock device"  error messages still occurs (Been there since intrepid).
I have fixed it with:
sudo killall gvfs-gphoto2-volume-monitor
sudo chmod -x /usr/lib/gvfs/gvfs-gphoto2-volume-monitor

-Camera - Kodak EasyShare DX6490 - usb connection
Irritating, as without the above you have to remove the memory card from the camera and slot it in a USB card reader.
F-spot now works after the above commands but the camera is not listed with the devices under Menu - Places - Computer

Good points:
I like the window buttons on the left!
Webcam and Skype work out of the box
Simple Scan is wonderful
TV tuner - DVB-T works (of course - needed to install firmware with System - Admin - Hardware Drivers and generate a channels.conf with w_scan)

---

### Post by mcooke1 on 2010-03-22
I have the same compiz problem as you regarding the 4 desktops I noticed it in the alpha and its still in the beta. I can get it to stay on 3 but not 4. Must be a bug.

---

### Post by Nightstrike2009 on 2010-03-22
It is a bug it occured with a previous version of Ubuntu.

The workaround for problem 1 is right click panel selector at left side of bottom bar (next to trash), select preferences, change columns to 4, (leave rows at 1), then click close.

Hardware drivers is for proprietary drivers. Ubuntu 10.04LTS beta uses the open-source 3d driver as the fglrx (closed source driver) has only just been made availabe by ATI but isn't compatible with 10.04 (yet devs are working on this now)

PS: Sorry I can help with problem 2, but your halfway there now ;-)

---

### Post by BrokeMahPC on 2010-03-22
Thank you nightstrike - your work around on the panel selector does the trick!

---

