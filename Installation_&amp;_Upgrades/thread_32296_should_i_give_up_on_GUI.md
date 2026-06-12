---
title: "should i give up on GUI?"
date: 2005-05-06
forum: Installation &amp; Upgrades
---

### Post by tAK on 2005-05-06
ok guys,

i have asked about this on the forums for help before, and never got a working answer. so im going to ask again. and im not going to stop asking until someonw points me in the working direction, or i stumble across it myself. !!!!

i dont get a GUI on first boot, it comes to the ubuntu console in text mode, i can log in, and have worked out a few things, such as IM with no gui... but im starting to get sick of it... i want my GUI

here are the platforms that i have tried this on, if someone has EVER had it working on one of these setups, or something extremely close, please let me know what you did, and put it into idiot terms so i dont have to keep asking quetions:

the hardware setups

1. AMD AthlonXP 2600+
ABIT NF-7m mainboard
Gf4 MMX 440 128Mb Onboard video
512Mb RAM (dual channel)
160Gb IDE hdd SEAGATE

2. AMD 64 2800+
Gigabyte mainboard (cant remember onboard graphics, but they didnt work, via ones from memory)
also with AGP Sparkle 6600GT card
200Gb SATA
40Gb IDE (tried both drives)
512Mb RAM

3. DELL Optiplex GX150
1Ghz intel p3
Intel onboard graphics (i810 or i820 from memory)
256Mb RAM
10Gb hdd

my final choice for a try, is my latest machine:
4. AMD64 3500+ skt 939
1Gb Corsair RAM
SPARKLE PCI-e 6600GT 128Mb card
200GB SEAGATE SATA
DFI LANPARTY NF4 ULTRA - D

if anyone has gotten any of this hardware working with any of this hardware, please let me know, as i damn well cant... at the moment, i still have an install on the dell

so, if you have any little idea that might help, let me know, so far, i have tried the manually reconfig the xfree86, but it doesnt work, my major point to show here, is that the live CD works 100% on all of these systems, and it gets a GUI, so why can it configure the graphics properly, but the isntaller cant?

plese help if you can, im getting to the end of my tether, but after trying the live CD over 2 months ago, i seriously want to run a desktop system in my house with ut for all of my non gaming needs

(side note: Debian also does the same thing with its gui , however Xandros, linspire, redhat 6. fedora core 2/3. SUSE 9.0 and MEPIS (im never touching it again) all worked 100% straight out of the box... i thought ubuntu was meant to be a user friendly distro... 2 months worth of effort have gotten me now where...  ](*,) )

/tAK

---

### Post by DJ_Max on 2005-05-06
XFree86 isn't really supported much on Linux distributions, any longer. You may wanna try to upgrade to Hoary, which uses Xorg. Then I would be able to help.

---

### Post by ltmon on 2005-05-06
Hi,

Can you try typing at console:

startx > output.txt &2>1

and then when you get returned to the console (I assume this is what occurs) posting the contents of output.txt.  This might give people here a bit more of an idea about what is going on.

Cheers,

L.

---

### Post by stream303 on 2006-01-16
As for the Dell GX150:

After installation, change the default color depth in /etc/X11/xorg.conf down from 24 to 16.  This way you get to keep your desired resolution - at least video is usable and stable...

---

### Post by ardchoille on 2006-01-16
Your first machine listed is almost identical to one of my machines, except that I never use onboard video - I always buy nvidia cards - and I have run several distros and never was I dumped into a command prompt after logging in.

---

### Post by newuser111 on 2006-01-16
tak have you ever tried running sudo dpkg-reconfigure xserver-xfree86 and selecting VESA as the display driver?

---

