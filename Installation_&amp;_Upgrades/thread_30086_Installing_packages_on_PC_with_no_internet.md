---
title: "Installing packages on PC with no internet"
date: 2005-04-27
forum: Installation &amp; Upgrades
---

### Post by leezer3 on 2005-04-27
Hi all,
Finally got Ubuntu working perfectly, only to find that I need a couple of new packages to play DVDs & listen to my MP3 collection. The problem comes, as these are on the internet, and try as I might, I can't get Ubuntu to recognise the modem in this machine. (Toshiba Software Modem AMR) This means that I want to download & install these packages manually. Now, I've got several packages on my desktop; First concern is that they're only about 30-40 kbs, seems small. Secondly, double-clicking on them only gives me FileRoller, which obviously don't open them :P
Need some info on how to proceed from here please.

Thanks

Leezer

---

### Post by fordfan753 on 2005-04-27
Double clicking them??
Just use your gnome terminal
# dpkg -i [package]
and if it comes up with a dependency issue then install the package(s) it's asking for (the same way) and retry.

---

### Post by leezer3 on 2005-04-27
Sorry  :)  Couldn't find the manual package install command anywhere; Double clicking only gives FileRoller, which doesn't open them. 
Double clicks DO NOT work by default (Entirely vanilla system)- Need the correct app/ command, which I obviously didn't know.

Thanks.

-Leezer-

---

### Post by az on 2005-04-27
Since these packages are not part of the repository, you must install them "by hand"

Open a terminal and change directory to where the package is and then use dpkg

example:

cd Desktop
sudo dpkg -i <package-2.3.4.deb>

---

### Post by leezer3 on 2005-04-29
Moving on; Now have wireless, but no modem. I've installed all required packages by hand, & now I actually have mp3s etc, but Xine doesn't want to recognise DVDs (And yes, I've installed libdvdcss!). Also seem to have wrecked my boot time; Oh well on to fiddle :D

-Leezer-

---

### Post by snairofilac on 2005-05-21
here's the thread where I got my DVD's working in XINE.

[http://www.ubuntuforums.org/showthread.php?t=35261](http://www.ubuntuforums.org/showthread.php?t=35261)

i was told to add the version of libcss that is included in the backports repository instead of the one i had already installed from the disk.

instructions to add backports can be found at 
[http://www.ubuntuguide.com](http://www.ubuntuguide.com)

gl

---

