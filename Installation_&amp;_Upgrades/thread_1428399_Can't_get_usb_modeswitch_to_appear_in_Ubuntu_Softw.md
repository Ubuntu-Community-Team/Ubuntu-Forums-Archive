---
title: "Can't get usb_modeswitch to appear in Ubuntu Software Centre"
date: 2010-03-12
forum: Installation &amp; Upgrades
---

### Post by new2ubun2linux on 2010-03-12
I am having a problem getting my Vodafone PAYG Huawei K3565 Rev 2 mobile broadband to be recognised and/or connect in 9.10

Reading round the forum I have come to the conclusion I need to try installing usb_modeswitch. Now comes my simple problem. Looking on

[http://packages.ubuntu.com/karmic/i386/usb-modeswitch/download](http://packages.ubuntu.com/karmic/i386/usb-modeswitch/download)

The advice is to add

deb [http://cz.archive.ubuntu.com/ubuntu](http://cz.archive.ubuntu.com/ubuntu) karmic main universe

to the apt sources. (replacing cz as required for several other servers of choice). I tried this (using several different servers) from within Ubuntu Software Centre, but the usb_modeswitch never appeared. In fact (oddly) the source never appeared in the list! (Although I did have a look in the etc/apt/sources.list and it had added a line each time - there were several - I'd tried quite a few!!!) I did try downloading it but when it starts gdebi to install, a message pops up saying it is available (and better supported!) in a software channel.

I searched round a bit and found another reference to the package at

[http://packages.debian.org/sid/i386/usb-modeswitch/download](http://packages.debian.org/sid/i386/usb-modeswitch/download)

This time the sources were totally different and the apt line recommended was

deb [http://ftp.de.debian.org/debian](http://ftp.de.debian.org/debian) sid main

When I add this it *does* add the line to the list of sources, but sadly I still cannot see usb_modeswitch after Software Centre has updated. In fact the number of packages available seems to go *down* from 2186 to 2179!

I suppose I could force the debian package to install, but I don't see why I can't get it to appear in Software Centre!

I should perhaps add that I have added other sources using the "apt sources" and that worked OK so I know I am doing the right thing.

Any ideas anyone...

---

### Post by chrisp1000 on 2010-03-13
Install the one you downloaded, that is what I did, though I haven't got my connection working yet so that could be one of my probs.

---

