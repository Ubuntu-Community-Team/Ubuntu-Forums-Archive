---
title: "Help! part way there ? Scanner &amp; webcam . . ."
date: 2008-07-22
forum: Installation &amp; Upgrades
---

### Post by larry19l on 2008-07-22
Hi Folks,

8.04 Hardy

Xsane doesn't find scanner.

scanimage produces this:
scanimage: open of device v4l:/dev/video0 failed: Invalid argument

lsusb gets me this info(other stuff left out): 
Bus 002 Device 011: ID 04a9:2225 Canon, Inc. CanoScan LiDE 70<-scanner
Bus 002 Device 008: ID 046d:08c9 Logitech, Inc. <--------------webcam

Added this to /etc/sane.d/genesys.conf
# Canon LiDE 70
#(added 7.22.2008)
usb 0x04a9 0x2225

But STILL getting this from xsane, after "scanning for devices",
Error: Failed to open 'v4l:/dev/video0': Invalid argument.

Am I supposed to do anything else ?

It would be nice to get both scanner & webcam working.

Anyone ?

---

### Post by Sef on 2008-07-23
Check out the [sane-project]("http://www.sane-project.org/cgi-bin/driver.pl") for your scanner.

In the future, please provide specs for your computer and types of equipment that you have.

---

### Post by larry19l on 2008-07-23
> **Sef said:**
> Check out the [sane-project]("http://www.sane-project.org/cgi-bin/driver.pl") for your scanner.


The scanner is a Canon LiDE 70 which the sane-project lists as unsupported.
It's been unsupported for quite a while now, but I don't have the time now to dedicate to learning how to write a backend so I'm looking for help to set up things as if it were a LiDE 60. If that provides basic functionality, I can get by for now and write the backend later.
As to hardware, it's a usb scanner and it will be switched between several Ubuntu machines running 8.04 from the LiveCD downloaded about 4 weeks ago.

If you want more info from other detection programs, give me the code.
I switched it to a different usb port so the previous locations I listed are no longer the same. Just different device numbers.
---
BTW Cheese works fine for the webcam, Camorama doesn't: Error, could not connect to video device: /dev/video0. So I gotta find out what Cheese is connecting to. Later on that.

---

