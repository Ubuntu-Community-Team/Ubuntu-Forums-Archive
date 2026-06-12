---
title: "Acer Aspire One Ubuntu USB Install?"
date: 2012-01-29
forum: Installation &amp; Upgrades
---

### Post by MagnetsNextToMotherboard on 2012-01-29
I've been trying to install Ubuntu 11.10 Desktop AMD 64-bit onto my Acer Aspire One Netbook via USB stick because I don't have a DVD drive on it, for a while now and so far everything I have tried hasn't worked.

First I tried installing it by using the Universal USB installer 1.8.7.9, making a pen-drive with the ISO "ubuntu-11.10-desktop-amd64" and going into the bios and selecting my USB stick as the primary boot device. I got this on a black screen with white text, nothing happens afterwards.

"SYSLINUX 4.05 EDD 2011-12-09 Copyright (c) 1994-2011 H. Peter Anvin et al"

The second time I downloaded a torrent of the "ubuntu-11.10-alternate-amd64" from the Ubuntu site, used the USB installer and made a pendrive, with the same settings in my bios using the USB stick as my primary boot device. This time I got a menu with the Ubuntu logo and "Ubuntu,", I had the options of running Ubuntu from the USB stick, booting from the hard drive, installing Ubuntu, testing memory and maybe some others but I can't remember. First I navigated down with my arrow keys to the option of installing, and I pressed "Enter" ... The menu text flashed, and nothing happened, so I pressed again and still nothing, then I tried all of the options, the only thing I could do was look at the "Help" menu and do the memory test. 

The third time, I saved all my important files to my desktop by removing the hard drive from my netbook and pluging it into my desktop. Then I formatted, and tried installing Ubuntu via USB stick with the version: "ubuntu-11.10-desktop-amd64" and still I got the error:

"SYSLINUX 4.05 EDD 2011-12-09 Copyright (c) 1994-2011 H. Peter Anvin et al"

So... At this point I have a netbook with no operating system, and have no idea how to get Ubuntu loaded onto it. Thanks for help in advanced.

---

### Post by 2F4U on 2012-01-29
What is the exact model and the hardware specs? This site documents how to install Ubuntu on several Aspire One models:

[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

And here is some information on how to troubleshoot black screen issues:

[https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen](https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen)

---

### Post by MagnetsNextToMotherboard on 2012-01-29
The model is a newer (2011 I believe) Acer Aspire One 722, specifications are:

AMD C-50 APU (GPU and CPU)
4GB RAM
500GB Hard Drive

---

### Post by MagnetsNextToMotherboard on 2012-01-29
None of these guides are the Aspire One 722 for 11.10 :/

---

### Post by 075360 on 2012-02-03
I have exactly the same problem. I tried to replace Windows 7 with Ubuntu I tried different relases using both UniversalUSB (1.8.7.9) and Unetbootin (563) I am still unable to install it.

All I can see is SYSLINUX copyright and only hard restart can fix it. 

I have Acer Aspire One 722 C-52

Any ideas?

---

### Post by serge_o on 2012-02-05
this is a known problem with all netbooks.
you will need a linux computer to fix this
see
[http://ubuntuforums.org/showthread.php?t=1610031](http://ubuntuforums.org/showthread.php?t=1610031)

the last two posts

you basically have to copy the iso directly onto the usb stick, not using the windows usb universal thing or the ubuntu program.
this is easy and done in one line in the console

it works ok afterwards.

you just need a working linux machine somewhere to do this.

if you have any more questions just ask

---

### Post by serge_o on 2012-02-05
by the way unetbootin won't help. no program will help. netbooks are "special" in that they need a very special USB stick that no program ( I know of) can make, except for the advice above.

the same advice goes for the topic starter

---

### Post by v8metal on 2012-03-19
I had the same problem with Acer AO722. I used "LinuxLive USB Creator 2.8.10" on Win7 and I installed Ubuntu 11.1 without any problem!!!! :guitar:

---

