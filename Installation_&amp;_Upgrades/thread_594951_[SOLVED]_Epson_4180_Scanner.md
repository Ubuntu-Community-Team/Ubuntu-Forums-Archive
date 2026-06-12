---
title: "[SOLVED] Epson 4180 Scanner"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by measekite on 2007-10-28
**Does anybody have a working Epson Perfection 4180 Scanner working with Feisty?  If so please post a step by step approach.**

I saw the links for iscan and have read mixed posts of if they work or not.  I have also seen many posts on changing various conf files.  It seems that nobody has actually posted a step by step for this scanner and Feisty.

In the Xsane listings there is no entry for the 4180 but only for the 4800 and the 3400 series.  I thought the 4180 was a popular scanner.  I have had no problems under windows except the scanning software was poorly designed but it worked.

I have googled and seen most of the links having to do with this and the docs are not clear and :confused:ing.

---

### Post by linuxwizard on 2007-10-28
That scanner is not supported by Sane.
[http://www.sane-project.org/sane-mfgs.html#Z-EPSON](http://www.sane-project.org/sane-mfgs.html#Z-EPSON)

But I was doing some searching you might be able to use the driver from here. It show Perfection 4180. You will have to figure out if this will work for you.

[http://www.avasys.jp/english/linux_e/dl_scan.html](http://www.avasys.jp/english/linux_e/dl_scan.html)

---

### Post by measekite on 2007-10-28
> **linuxwizard said:**
> That scanner is not supported by Sane.
[http://www.sane-project.org/sane-mfgs.html#Z-EPSON](http://www.sane-project.org/sane-mfgs.html#Z-EPSON)

But I was doing some searching you might be able to use the driver from here. It show Perfection 4180. You will have to figure out if this will work for you.

[http://www.avasys.jp/english/linux_e/dl_scan.html](http://www.avasys.jp/english/linux_e/dl_scan.html)


Already been to the second link Epson AVASYS

What I find it difficult to believe is that all of the Perfections are there except for the 4180.  

Do you think that omission was an oversight.

Do you think that the 4180 takes the same driver as

the 3490 and 3590 since the ID is 0x0122

or 
the 4870 that has an ID of 0x0128

They are similar machines.

---

### Post by linuxwizard on 2007-10-28
No I don't think it is a oversight. Their is something different with the 4180 that is why it is not supported. I have a HP scanner not supported but 2 other models that are close to mine they are supported. The only difference between them and mine is that i have an adapter to use to scan 35mm pictures. So what I am getting at is there is a feature in yours that they can not come up with a driver that will work or to use in linux or adapt into linux.

---

### Post by measekite on 2007-10-28
> **linuxwizard said:**
> No I don't think it is a oversight. Their is something different with the 4180 that is why it is not supported. I have a HP scanner not supported but 2 other models that are close to mine they are supported. The only difference between them and mine is that i have an adapter to use to scan 35mm pictures. So what I am getting at is there is a feature in yours that they can not come up with a driver that will work or to use in linux or adapt into linux.


I do see your point.  But if all I do is regular vanilla scanning without using any off track feature do you think a driver for a similar model might work for most of the features with that exception?

I would have to purchase another scanner when this one is a real good one.  Scanning is a requirement for me.

I would hate to save up a batch of scans and boot to windows.  I am trying to leave windows behind except for .net programming.

---

### Post by linuxwizard on 2007-10-28
If you want to try to get a driver to work I would see what you can do with this one.
[http://www.avasys.jp/english/linux_e/dl_scan.html](http://www.avasys.jp/english/linux_e/dl_scan.html)

I save up things to scan than use xp. I need to buy a new scanner.

---

### Post by useslack on 2007-10-31
This scanner and iscan definately work under linux (software is functional if not as good as other sane frontends).  I have it working under Slackware 10.2.  I'm not a Kubuntu guru, but intend to have a crack at getting this going this week otherwise the scanner has to go back downstairs and onto the slackware box so I can scan some photos.
  From my previous research I believe this is not a true Epson scanner and has a different instruction set to other epson scanners which is why every other Epson apart from the one I/we bought works and this one is a royal pain!! n.b. I think that the avasys stuff is closed source in case this upsets your principles!

---

### Post by measekite on 2007-10-31
> **useslack said:**
> This scanner and iscan definately work under linux (software is functional if not as good as other sane frontends).  I have it working under Slackware 10.2.  I'm not a Kubuntu guru, but intend to have a crack at getting this going this week otherwise the scanner has to go back downstairs and onto the slackware box so I can scan some photos.
  From my previous research I believe this is not a true Epson scanner and has a different instruction set to other epson scanners which is why every other Epson apart from the one I/we bought works and this one is a royal pain!! n.b. I think that the avasys stuff is closed source in case this upsets your principles!

[SOLVED]

I found a solution to the problem.  My Epson Perfection 4180 Photo Scanner ()aka Epson GT600) now works with both XSane and Quiteinsane great.  I prefer XSane since I can create mutiple image PDFs in a breeze.

You may not need to do everything.

I went to the Epson AvaSys site and downloaded 2 rpm files.  I converted them to DEBs.

I attatched the plugin file.  You can download the other file (imagescan) if you need it.

If the attachement did not upload
goto [http://www.avasys.jp/english/linux_e/dl_scan.html](http://www.avasys.jp/english/linux_e/dl_scan.html)

and download
**iscan-plugin-gt-f600-1.0.0-1.c2.i386.rpm**
and use alien to convert it to a deb and then install it or install it from the rpm using 

[COLOR=Green]**alien -1 iscan-plugin-gt-f600-1.0.0-1.c2.i386.rpm**[/COLOR]


I first used alien to install the imagescan file and got some overwrite errors so I am really not sure if any important part got installed.  The scanner did not work upon doing this.

After executing the plugin file (I attached it as a deb) I then found the epkowa.conf file in the sane.d folder (Unbuntu Feisty) and it did this:

**/etc/sane.d/epkowa.conf**

```
# epkowa.conf -- sample configuration for the EPKOWA SANE backend
# Copyright (C) 2004  Olaf Meeuwissen
#
# See sane-epkowa(5), sane-scsi(5) and sane-usb(5) for details.
# On systems with libusb, the following line is sufficient to get the
# backend to recognise your USB scanners.  It presumes, however, that
# the scanner---more precisely, it's USB product ID---is known to the
# backend.
# For all USB scanners that are officially supported by this backend,
# this presumption is true.  A list of such scanners can be found in
# sane-epkowa(5).
#
#usb
# For any USB scanner not known to the backend (yet), you may, at your
# own peril(!!), force the backend to recognise and use it via libusb.
# You can do so by the following configuration command:
# 
#   usb <USB vendor ID> <USB product ID
usb 0x04b8 0x0118

```You may or may not have to edit the file.  Make sure everything else is commented out.  I also edited epson.conf in the same folder and commented everything out.

XSane was executed from the menu and found the scanner.  It works great.

You can even access it from The Gimp and the scans will go directly into The Gimp editor it you access it that way.

All the features of the scanner works with XSane.

Once you know what to do and where to get the driver it is a 10 minute job and is easy.

Sorry this is so long but I wanted to make sure anybody who has this scanner will not have to endure the aggravation I did to get the job done.

Now I need to foucs on the Canon IP4000 printer so I can produce a print form Linux Gimp that I was able to with Windows Gimp and Photoshop.:-D:-D:-D:-D

---

### Post by regomodo on 2007-12-12
hmm didn't work for me in debian. maybe it's due to --force-architecture for amd64 but i can't see that making a difference

---

### Post by regomodo on 2008-03-04
just tried again. That worked in Debian Etch i386! Albeit as root

If only i could get it working under amd64. Things are slowly coming together. PS CS2, now this.

---

