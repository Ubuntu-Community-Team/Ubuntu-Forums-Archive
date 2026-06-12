---
title: "Need help installing USB drivers"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by Nekativ on 2009-11-13
Hi, I am rather new to Linux and do not know what to do.

I need to install ftdi_sio drivers to run a USB to Serial adapter. The drivers page is linked below:

[http://ftdi-usb-sio.sourceforge.net/](http://ftdi-usb-sio.sourceforge.net/)

I un-gz/tar the only files that are extracted are

ftdi_sio.c

and

ftdi_sio.h

Well, I have been searching all day and cannot seem to figure out what to do with the files. 

I did get these general instructions tho:

"The Linux FTDI USB driver provided is version 1.2.1.  More information on the driver, 
including updated versions can be found at [http://ftdi-usb-sio.sourceforge.net/](http://ftdi-usb-sio.sourceforge.net/).  The driver 
should be compiled either as a loadable module or into a kernel.  The PID should be changed in the header file to "0xEE18" which corresponds to the PID used 
on FTDI USB Converter in the MaxStream PKG-U.  "

These instructions do not come with the default drivers that you can download from sourceforge.net

Any help would be appreciated as I have been searching all day.

---

### Post by Nekativ on 2009-11-13
bump, wow these forums move fast :P

---

### Post by hal10000 on 2009-11-14
you don't ned to install it, it's already installed by default.
Just plug in your device and verify if the driver is loaded by typing on a terminal window:
```
lsmod | grep  ftdi_sio
```
Id you get an answer, then it's loaded. If you don't get an answer, try
```
 sudo modprobe ftdi_sio
```
This will load the driver.

That's all you (hopefully) need.

---

### Post by Nekativ on 2009-11-17
> **hal10000 said:**
> you don't ned to install it, it's already installed by default.
Just plug in your device and verify if the driver is loaded by typing on a terminal window:
```
lsmod | grep  ftdi_sio
```Id you get an answer, then it's loaded. If you don't get an answer, try
```
 sudo modprobe ftdi_sio
```This will load the driver.

That's all you (hopefully) need.


Thank you very much, works like a charm :)

---

### Post by hal10000 on 2009-11-17
If you boot next time and it is not loaded automatically, then make (as root) an entry into your **/etc/modules** file. Just put **ftdi_sio** at the end of the file.

Modules in this file will be loaded at boottime

---

### Post by dhavalbbhatt on 2009-11-17
Can you please mark this as solved? It would help others.

Thanks,
DB

---

### Post by asujan6 on 2009-11-17
[glassware]("[http://www.atoncer.com/glassware/main.htm")(http://www.atoncer.com/glassware/main.htm"]glassware[/url)]
[used](http://www.atoncer.com/dvd-movies/main.htm"]used) dvd movies]("[http://www.atoncer.com/dvd-movies/main.htm")
[jewelry]("[http://www.atoncer.com/jewelry/main.htm")(http://www.atoncer.com/jewelry/main.htm"]jewelry[/url)]
[used](http://www.atoncer.com/musical-instruments/main.htm"]used) musical instruments]]("[http://www.atoncer.com/musical-instruments/main.htm")
[bears](http://www.atoncer.com/bears/main.htm"]bears) collecting]("[http://www.atoncer.com/bears/main.htm")

---

### Post by asujan6 on 2009-11-17
[glassware]("http://[http://www.atoncer.com/glassware/main.htm")(http://www.atoncer.com/glassware/main.htm"]glassware[/url)]
[used](http://www.atoncer.com/dvd-movies/main.htm"]used) dvd movies]("http://[http://www.atoncer.com/dvd-movies/main.htm")
[jewelry]("http://[http://www.atoncer.com/jewelry/main.htm")(http://www.atoncer.com/jewelry/main.htm"]jewelry[/url)]
[used](http://www.atoncer.com/musical-instruments/main.htm"]used) musical instruments]]("http://[http://www.atoncer.com/musical-instruments/main.htm")
[bears](http://www.atoncer.com/bears/main.htm"]bears) collecting]("http://[http://www.atoncer.com/bears/main.htm")

---

