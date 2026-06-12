---
title: "Ide_intr error on booting"
date: 2006-06-22
forum: Installation &amp; Upgrades
---

### Post by fnando on 2006-06-22
I'm trying to install (clear install) Dapper Final Release.

Here's the error:

hdc: ide_intr: huh? expected null handler on exit
Buffer I/O error on device hdc, logical block 357296

My config:

DVD-RW Samsung (bought 2 days ago)
ASUS A8N-SLI
AMD64 Venice 3700+
1 GB RAM Samsung
Radeon X300 256mb
HD 120GB Samsung
HD 20GB Seagate

I checked the CD for errors and everything is ok.

Any tip?

---

### Post by Turtle.net on 2006-10-19
I have exactly the same problem with edgy (release candidate). But i never had this bug with any other ubuntu release ... ????
I filled a bug in launchpad [https://launchpad.net/distros/ubuntu/+source/casper/+bug/66850](https://launchpad.net/distros/ubuntu/+source/casper/+bug/66850)

I hope that will help

---

### Post by myleftfoot on 2006-11-08
Hi get the same error. I have a new system that I have built with the ASUS A8N-SLI Deluxe

The Error I get after a long pause is

-----
[999.9999]hdc: ide_intr: huh? expected NULL on exit
[999.9999]Buffer I/O error on device hdc, logical block 3556648
-----
These two lines and only these too lines repeated over and over.

My System
----------
[ASUS A8N-SLI Deluxe]("http://usa.asus.com/products.aspx?l1=3&l2=15&l3=148&model=375&modelmenu=2") - BIOS Revision 1016
AMD 64 X2 4600+
3 GB of DDR 400 Memory
160 Gbytes HD - Seagate Barracuda 7200.7, model ST3160023A
NVidia GeForce 7300 GS
----------

The hardware works because I currently have Windows Vista RC 1 on it. I just wish it had ubuntu linux too...

---

### Post by ohGrbyte on 2006-11-18
I've been having the same problem also. In a previous thread on this, someone said to try using the Alternate ISO. So I am going to try that. 

My System:
AMD Sempron 3400 2.0ghz
512MB (shared w/ Nvidia Video)
Nvidia Geforce 6100
160 GB Harddrive Seagate Barracuda (wow I'm not the only one go figure).

So far it's only  been the Ubuntu cd. However I've been able to get Kubuntu to boot up and install with no problem what so ever.
I just don't care for KDE much.

If I get the Alernate CD to work (downloading the 64Bit version), I will post back.

---

### Post by ohGrbyte on 2006-11-18
Success!

The Alternate ISO worked. I was able to install Ubuntu using the OEM Install Selection. Installed with no errors or problems. I did notice one disappointing problem once I was able to log on, the performance was poor, especially moving around windows and such. 

So I have a fix for that, if anyone encounters it.

I installed the Nvidia drivers and Beryl (which is real nice btw).
Now everything runs smoothly, and pretty too :mrgreen: 

I used this Howto from the forums to do it.
[http://ubuntuforums.org/showthread.php?t=263851&highlight=HOWTO%3A+Latest+NVIDIA+drivers]("http://ubuntuforums.org/showthread.php?t=263851&highlight=HOWTO%3A+Latest+NVIDIA+drivers")

It was pretty straight forward, no bumps in the road basically.

So I hope helps,

---

