---
title: "Trouble with Logitech QC Express Plus"
date: 2006-09-02
forum: Installation &amp; Upgrades
---

### Post by emmi on 2006-09-02
Hi, I'm having a big trouble trying to get my Webcam to work in my Dapper Drake 6.06.

It just can't get it to work.

When I type lsusb i get:
> Bus 002 Device 006: ID 046d:092f Logitech, Inc.

I've install xawtv and when i run that this appear:
> can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available


Does anyone know what is the problem or doesn't it support this camera?

---

### Post by keplerspeed on 2008-07-18
I have a logitech quickcam, with a lsusb i get:

Bus 002 Device 005: ID 046d:092f Logitech, Inc. QuickCam express Plus

but same as emmi, when i run xawtv, even as root it says:

v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available

and with camorama, also as root:

could not connect to video device (/dev/video0)

the interesting thing is that i had my webcam working. months ago. but i now have a pinnacle usb tv tuner and followed a tutorial, unfortunatley cant remember the url, and since i got the tv tuner working the webcam has given me these errors. i have found numerous solutions, with no effect. atleast we are not alone!!

---

### Post by keplerspeed on 2008-07-18
I have a logitech quickcam, with a lsusb i get:

Bus 002 Device 005: ID 046d:092f Logitech, Inc. QuickCam express Plus

but same as emmi, when i run xawtv, even as root it says:

v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available

and with camorama, also as root:

could not connect to video device (/dev/video0)

the interesting thing is that i had my webcam working. months ago. but i now have a pinnacle usb tv tuner and followed a tutorial, unfortunatley cant remember the url, and since i got the tv tuner working the webcam has given me these errors. i have found numerous solutions, with no effect. atleast we are not alone!!

---

