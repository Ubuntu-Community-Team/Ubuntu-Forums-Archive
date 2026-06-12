---
title: "32 bit Epson 3170 on 32 bit ubuntu 18.04 seen by scan programs but can't start scanne"
date: 2020-08-21
forum: Installation &amp; Upgrades
---

### Post by mikeprosceo-frontiernet on 2020-08-21
I put 32 bit  ubuntu 18.04 on my 64 bit computer so I could download the 32 bit  drivers for epson 3170 scanner.  I gave up trying to get it to work in  64 bit mode.  Skanlite and simple scan both see the scanner but cannot  start scanner.  Image scan does not see the scanner.  lsusb and   sane-find-scanner see epson flatbed scanner
 sudo scanimage -L
device `epson:libusb:001:003' is a Epson x-gnu/libsystemd  flatbed scanner
 scanimage -T
scanimage: sane_start: Invalid agrument
 scanimage -V
scanimage (sane-backends) 1.0.27; backend version 1.0.27
 cat /etc/sane.d/dll.conf  - commented out epson2 and epkowa
 Can anyone please help me.  I have been googling and searching for an answer, trying everything that is recommended.
 Xsane also sees my scanner (linux-gnu/sane/l flatbed scanner {epson:

libusb:001:002} and also sees it as  a network scaner {net:localhost:epson:libusb:001:002}   but with both I get the Error: Failed to start scanner:Invalid  argument.  Running it in terminal gives me the warning that I am on my  own if I try it and then I get the same error message: Invalid argument.  Any one have any ideas?

---

### Post by CelticWarrior on 2020-08-21
So, in the end, the same result. Meanwhile you wasted some time installing a "crippled" OS that's just about to be binned to the history's trash can for good. Even if you really needed a 32-bit OS having it in a virtual machine would be a more sane approach.

What about Windows? Does it still work with at least one of the currently supported Windows versions (8 and 10)? If so, again, virtual machine.

---

### Post by mikeprosceo-frontiernet on 2020-08-22
I installed it on a 32 bit system because I couldn't get any help trying to install it on my 64 bit system.  It is a good photo scanner and I wanted to be able to use it from my desktop.  The scanner works on my wife's Mac but I was hoping to get some help here instead of criticism.  The OS although old is on an older computer with only 2meg ram.  I see a lot of people have gotten it to work but I follow their suggestions with no luck.  Just looking for a little help here.  I thought ubuntu was supposed to be a simple easy OS.

---

### Post by CelticWarrior on 2020-08-22
Ubuntu is simple but doesn't do miracles. And 32-bit architecture is as good as dead. If you think that stating facts is criticism you better adjust your sensitivity meter ;-) as that was NOT the point.

---

### Post by SeijiSensei on 2020-08-22
Try VueScan.  [https://www.hamrick.com/](https://www.hamrick.com/)

---

### Post by mikeprosceo-frontiernet on 2020-08-22
I know ubuntu 18.04 is at its end and I know 32 bit has seen its day but since I can't get the scanner working on 64 bit thought since the scanner drivers were 32 bit it might be easier to get it working.  I figured I'd dedicate this computer just for scanning.  I guess not.

---

### Post by mikeprosceo-frontiernet on 2020-08-22
I had tried vuescan on 64 bit and was told by the tech team there that they didn't have the drivers either and couldn't help me.  I guess I will try it on 32 bit and see what happens.  Thanks

---

### Post by CelticWarrior on 2020-08-22
> **mikeprosceo-frontiernet said:**
> I had tried vuescan on 64 bit and was told by the tech team there that they didn't have the drivers either and couldn't help me.  I guess I will try it on 32 bit and see what happens.  Thanks

It's a waste of time.
VueScan doesn't have a different set of drivers just for 32-bit.

---

