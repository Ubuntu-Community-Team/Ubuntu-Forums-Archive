---
title: "Installation failure: cannot find package zlib"
date: 2005-06-27
forum: Installation &amp; Upgrades
---

### Post by otakuj462 on 2005-06-27
Hello everyone, I'm a linux n00b trying to install ubuntu on a very old PC: P1 133 mHz, 64 MB EDO RAM, generic Matshita CD-ROM drive, plus a 3Com PCI ethernet card  and a D-Link Xtreme G DWL-G520 wireless network card. The goal is to use this computer as a wireless router, using the wireless card to receive a connection to the internet, and sending back out through the ethernet card to a desktop machine. I chose Ubuntu because it comes with working drivers for the D-Link card.
I'm trying to install by booting from the CD-ROM, but unfortunately I keep running into a problem during installation. When the installer tries to install the base system, it can't find a specific package called "zlib", and it aborts the step and takes me back to the main menu. It also returns an error message which recommends trying to burn the iso on a slower speed, so I did that, burning a new CD, taking the speed down from 24x to 4x, but the result was the same. The file is definitely there on the CD: I'm able to access it on my Windows box using Windows Explorer.
So my questions are these: Why might the installer be unable to see this file? Is there some way to fix it? If not, is there a way to install ubuntu onto a computer without a working operating system that does not involve booting from a CD? 
Thanks all.

-Jake

---

### Post by dialate on 2005-06-27
Your iso could have been a bad download. Make sure the md5sum is the same as it shows on the ubuntu download page.

If you're Windows only at this point,  you can use the program at [http://theopencd.sunsite.dk/md5sum.exe](http://theopencd.sunsite.dk/md5sum.exe)

Should be

f6b3f164c99761234858a4d2c12d0840 

if you downloaded ubuntu-5.04-install-i386.iso

---

### Post by srinath on 2005-09-07
How do I use this program? I did not understand. Could you please explain?

Thanks.

---

