---
title: "Can't install on Fit PC"
date: 2012-02-20
forum: Installation &amp; Upgrades
---

### Post by kahgfakhjsf on 2012-02-20
I'm trying to install Ubuntu 11 on an atom based fit PC but it doesn't work. 

I created a USB boot drive and configured BIOS to boot form USB. 

Ubuntu starts booting up but after a few seconds I get the following on the screen:
[http://www2.engr.arizona.edu/~weaverg/images/IMG_0003-small.JPG](http://www2.engr.arizona.edu/~weaverg/images/IMG_0003-small.JPG)
```
[42.900742] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
```

Then it goes to this screen:
[http://www2.engr.arizona.edu/~weaverg/images/IMG_0004-small.JPG](http://www2.engr.arizona.edu/~weaverg/images/IMG_0004-small.JPG)

And doesn't do anything after that. 

How can I get Ubuntu on my Fit PC?

---

### Post by youngunix on 2012-02-20
Can you provide your hardware specs?

---

### Post by jayshomebrew on 2012-02-20
Try this: check the nomodeset option when installing..
[IMG]http://img827.imageshack.us/img827/3509/dgfdgrunningoraclevmvir.png[/IMG]

---

### Post by kahgfakhjsf on 2012-02-21
This is the system I have: 
[http://www.fit-pc.com/web/fit-pc/fit-pc2-specifications/](http://www.fit-pc.com/web/fit-pc/fit-pc2-specifications/)

When I try the nomodset trick and I select "Try Ubuntu" I get put into a command prompt. When I install ubuntu: I get the same errors as before. 

Can I get ubuntu with the GUI?

---

### Post by youngunix on 2012-02-21
Judging from the specs you provided, you should try a light weight version of ubuntu. 
I'm running Ubuntu 11.10 on this: 
CPU: Intel Pentium E2200. LGA-775.
RAM: 2GB DDR2.
Graphics: Intel integrated.
HDD: 750GB 16MB-cache @7200RPM (I had to upgrade from 160GB-8MB-cache @5400RPM for ubuntu to work smoothly).

---

### Post by snowpine on 2012-02-21
Support for Intel GMA500 graphics is very poor in Linux.

More info here: [http://ubuntuforums.org/showthread.php?t=1229345](http://ubuntuforums.org/showthread.php?t=1229345)

---

### Post by jayshomebrew on 2012-02-21
how about trying the kernel boot option:
```
poulsbo.dummy=1 psb_gfx=1
```
hit *F6* at the welcome page, and then *ESC* then add the options at the end of the line.

more about ubuntu boot options:
[https://help.ubuntu.com/community/BootOptions]("https://help.ubuntu.com/community/BootOptions")

---

### Post by kahgfakhjsf on 2012-02-22
Thanks for all your input everyone. 

I actually got Debian to work on the fit PC. If I need to install Ubuntu: I'll follow the rest of the suggestions in this thread and let you all know how it goes.

---

### Post by gaby81 on 2012-08-06
Please add this to the kernel's bootargs
```
vga=31A
```
or
```
vga=315
```

---

