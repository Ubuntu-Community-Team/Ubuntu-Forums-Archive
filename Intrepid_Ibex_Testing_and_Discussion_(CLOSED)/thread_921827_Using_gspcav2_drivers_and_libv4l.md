---
title: "Using gspcav2 drivers and libv4l"
date: 2008-09-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Stemp on 2008-09-16
With Intrepid and kernel 2.6.27, here come the new gspcav2 drivers.

Unfortunately you can't use them with most of the applications.

The main reason is the lack of the libv4l library from Hans de Goede : [http://hansdegoede.livejournal.com/3636.html](http://hansdegoede.livejournal.com/3636.html)

The libv4l for Debian is waiting a mentor, so I uploaded it to my PPA for testing : 
```
deb http://ppa.launchpad.net/stemp/ubuntu intrepid main
```

This is a first step but unlike in Fedora 10 the applications are not patched so we need to call the different libs.

For applications that doesn't use v4l2 (eg camorama or skype) :
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so camorama
```

For v4l2 applications that doesn't handle webcam's specific pixelformats (eg cheese) :
```
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so cheese
```

---

### Post by plun on 2008-09-17
Thanks for taking time with this challenge... !

I have tested with an old Logitech cam which never worked before.

Detected as:
```
plun@plun:~$ lsusb
Bus 003 Device 002: ID 046d:0870 Logitech, Inc. QuickCam Express

```

Added your ppa and installed libv4l

What does this mean ?  (from Hans blog)

> Just replace open("dev/video0", ...) with v4l2_open("dev/video0", ...), ioctl with v4l2_ioctl, etc. libv4l2 will then do conversion of any known (webcam) pixelformats to bgr24 or yuv420.


Cheese fails but Camorama works.

Camorama must be started with **sudo priviligies**....:confused:


Thanks !

------------------

Fedoras specs was good:
[http://fedoraproject.org/wiki/Features/BetterWebcamSupport](http://fedoraproject.org/wiki/Features/BetterWebcamSupport)

---

### Post by Stemp on 2008-09-17
> **plun said:**
> Detected as:
```
plun@plun:~$ lsusb
Bus 003 Device 002: ID 046d:0870 Logitech, Inc. QuickCam Express

```


Are you sure this cam is using the gspca driver ?
I thought it was using the qc-usb !
I can't even find it on [gspcav2 webcam list]("http://moinejf.free.fr/webcam.html") 

```
lsmod | grep gspca
```

If it's using the gspca driver, please try [Jean-François Moine README]("http://moinejf.free.fr/gspca_README.txt").


> **plun said:**
> What does this mean ?  (from Hans blog)

Nothing important for us, it's for developpers ;)



> **plun said:**
> Cheese fails but Camorama works.

Camorama must be started with **sudo priviligies**....:confused:

I'm also confused.

---

### Post by plun on 2008-09-17
> **Stemp said:**
> Are you sure this cam is using the gspca driver ?
I thought it was using the qc-usb !
I can't even find it on [gspcav2 webcam list]("http://moinejf.free.fr/webcam.html") 

```
lsmod | grep gspca
```

If it's using the gspca driver, please try [Jean-François Moine README]("http://moinejf.free.fr/gspca_README.txt").



I'm also confused.

OK... lsmod gives nothing.

But something is loaded...:)

```
plun@plun:~$ lsmod | grep gspca

plun@plun:~$ dmesg


[   19.538472] Linux video capture interface: v2.00
[   19.620623] quickcam: QuickCam USB camera found (driver version QuickCam USB 0.6.6 $Date: 2006/11/04 08:38:14 $)
[   19.620630] quickcam: Kernel:2.6.27-3-generic bus:4 class:FF subclass:FF vendor:046D product:0870
[   19.647709] quickcam: Sensor HDCS-1020 detected
[   19.653943] quickcam: Registered device: /dev/video0
[   19.653982] usbcore: registered new interface driver quickcam


```

driver quickcam....:confused:


I have another camera "somewhere"  and test some more...  (if I find it :))


Thanks !

---

