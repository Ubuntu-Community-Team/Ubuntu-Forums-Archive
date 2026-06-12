---
title: "Installer errors - need help (first time install)"
date: 2006-12-13
forum: Installation &amp; Upgrades
---

### Post by b0le on 2006-12-13
***SOLVED - using alternate install and ATi Drivers***

Hi,

I just downloaded Ubuntu 6.1 x64 iso file ([http://mirrors.uwa.edu.au/ubuntu-releases/edgy/ubuntu-6.10-desktop-amd64.iso](http://mirrors.uwa.edu.au/ubuntu-releases/edgy/ubuntu-6.10-desktop-amd64.iso))

I burnt it to a cd (using Nero). The menu loads giving me some different options.

The first time I tried this, I loaded it normally (start or install), and during the loading the logo and bar was discoloured (only two or three colours (black white and grey/brown) - then a whole bunch of erros came up like this:

[numbers] Buffer I/O error on device hdb, logical block [more numbers]


I tried reburning the cd. After this I did CD Check (it was still discoloured) - after the loading bar filled up the computer restarted and then went back to the menu.I then selected safe graphics mode, then it came up with X-Server errors (here is some of it):



X Window System Ver 7.1.1
Release date: 12 May 2006
X Protocol version 11, revision 0, release 7.1.1
Build OS: Linux 2.6.15.7 x86_64
Current OS: Linux Ubuntu 2.6.17-10-Generic #2 SMP Fri OCt 13 15:34:39 UTC 2006 x86_64
...
(EE) - it says this means error - No devices detected
Fatal Server Error:
No Screens found                f"



In the advanced (?) details it said:
.....
(WW) The directory "usr/share/x11/fonts/..." does not exist (there was a lot of different sub directorys of fonts and a lot of warnings (WW))

(WW) PCI Mach64 in slot 1:0:0 could not be detected
(WW) PCI Mach64 in slot 1:0:1 could not be detected

Fatal Server Error:
No Screens found 




These text was in a deformed window (made up off a variety of characters). 

Here is my system:
Abit AN8-V Motherboard
ATi Radeon x800
AMD Athalon64 3200+
1gb of RAM (2x 512mb sticks)
DVD Burner from Pioneer
2 SATA HDDS

I have one empty HDD which is 160GB
The other 250GB one is partitioned into a 40GB drive (windows installed) and a 192GB drive (with all sorts of other stuff)

The first time I tried it I only had the 160GB hdd plugged in, and the second time I had both drives in.

I hope someone can help,

Thanks , Joel

---

### Post by b0le on 2006-12-13
After looking around the net a bit more I think that the error is caused by the graphics driver. However, the solution which I found:

Running this sudo dpkg-reconfigure xserver-xorg (and then changing it to VESA)

I don't think that can be done when ya install it (and if it can, I have no clue how.

Is it possible that this is the source of the error, and if so how would I fix it?

Thanks, Joel

---

### Post by nrgtek on 2006-12-17
I have the same problem with my ATI x800se PCI-e card. My installation freezes at the initial Ubuntu progress bar.

---

### Post by nrgtek on 2006-12-17
Just tried the alternate iso install cd, using text mode. kernel loads into memory and I just get"crc error system halted" 

what is it with this graphics card that won't install ubuntu. OpenSuse and Fedora install

---

