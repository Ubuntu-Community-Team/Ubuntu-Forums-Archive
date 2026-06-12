---
title: "Display server was shut down over 6 times ..."
date: 2008-02-26
forum: Installation &amp; Upgrades
---

### Post by papi-- on 2008-02-26
Hi everyone !

First of all im a real newbie, ive finished installing Ubuntu on my second laptop, but when booting it gives me : Display server as shut down over 6 times ...

Info of the computer im trying to install ubuntu into is :  

[http://alatest.fi/fujitsu_siemens_amilo_la_1703/kannettavat_tietokoneet/details/pd-34839582,30/?p=273411](http://alatest.fi/fujitsu_siemens_amilo_la_1703/kannettavat_tietokoneet/details/pd-34839582,30/?p=273411)

// Video Output / Graphics Processor

Vendor

VIA Chrome9 HC //


Ive installed ubuntu 7.10.



Can someone please help me ? :(

---

### Post by dstew on 2008-02-26
Try to get into a command line (actually, if the display server fails, it usually defaults to one). Enter```
sudo dpkg-reconfigure xserver-xorg
```Answer the questions the best you can. Try the vesa driver for the display. After configuring, enter **startx**. If you get a display, you can usually then try to install a restricted driver for your display using the Restricted Drivers Manager in System --> Administration.

What video display adapter does it have? If you don't know, post the output of **lspci**.
EDIT: I see it is a Via Chrome. So try the steps above, and see if you can at least get a desktop with the vesa driver. With that display adapter it might be a problem to get a good driver.
EDIT again: I see three driver packages that can be installed. They are xserver-xorg-video-via, xserver-xorg-video-unichrome, and xserver-xorg-video-openchrome. These are the unrestricted drivers. There might be others in the restricted drivers manager. The via driver might already be in there, and maybe that is the one causing the problems.

---

