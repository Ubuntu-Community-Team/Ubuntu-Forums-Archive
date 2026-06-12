---
title: "Install on Dell Inspiron 8100?"
date: 2006-11-07
forum: Installation &amp; Upgrades
---

### Post by SurferKauai on 2006-11-07
Is it possible to install Ubuntu-Linux on an old, Dell Inspiron 8100 laptop computer? I've been unable to find a URL that shows the basic instructions for how to do this.

Thanks.

---

### Post by ReaderRat on 2006-11-07
> **SurferKauai said:**
> Is it possible to install Ubuntu-Linux on an old, Dell Inspiron 8100 laptop computer? I've been unable to find a URL that shows the basic instructions for how to do this.
How much RAM do you have? What type of audio & video do you have? How large a HDD, and is there going to be another OS (Windblows) on it?

---

### Post by codypumper on 2006-11-07
Wanna just give us full system specs please?

---

### Post by ReaderRat on 2006-11-07
Specs were 256M RAM & 10 Gig HDD, so you should be able to run Ubuntu. I would suggest that you start with Dapper Drake (6.06). Edgy is a bit unstable and has laptop issues.installing. For your future reference:
Burning an ISO file:
**[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)**
[**Installing Ubuntu**](http://www.psychocats.net/ubuntu/installing)

---

### Post by Jbloudg20 on 2006-11-07
I used to use Mandrake on my (now deceased) 8100. It should run Ubunutu, it just might be a tad slow.

My old specs IIRC, were something on the order of:
1 GHz P3
256 MB Ram
40GB HDD
with some sort of Nvidia video chipset.

His specs should be in the ballpark of those.

---

### Post by K.Mandla on 2006-11-08
> **SurferKauai said:**
> Is it possible to install Ubuntu-Linux on an old, Dell Inspiron 8100 laptop computer? I've been unable to find a URL that shows the basic instructions for how to do this.
I've put Xubuntu on a half-dozen 8100s and all of them worked fine. GeForce video cards are more forgiving than the Radeon 7500s, but there's no real difference on stuff that old. (Shameless self-promotion: You can get it running on stuff that is [MUCH older]("http://www.ubuntuforums.org/showthread.php?t=294292"). :D )

If you have the 1600x1200 screen, you'll want at least the 32Mb GeForce2 video card. The 16Mb card has slow redraw rates at that resolution. Luckily, those cards run about $20 on ebay. A full-fledged 64Mb GeForce4 Go 440 MX is closer to $100, but worth it. I have one in my 8000 and love it.

And if you've got an extra $60 to spare, you can dump the full 512Mb of PC133 in those, and it's golden. If I remember right, the 8100 can hold processors up to 2Ghz+, and that means your machine is far from obsolete.

I've not worked with the MiniPCI wirless card; I use a WPC11 v3 -- it's a b-wireless card, but needs no configuration aside from the WEP key.

Have fun! You're going to love it!

---

### Post by SurferKauai on 2006-11-08
Thanks for responding;
RAM=256MB (Intel Pentium III; Mobile CPU 1000MHz)
Type of Audio: appears to be "ESS Maestro"
Video: I wasn't sure where to find the specs on this
HD Size= 23.2GB Free space (Win XP Home, Version 2002, Service Pack 2)

---

### Post by SurferKauai on 2006-11-08
> **K.Mandla said:**
> I've put Xubuntu on a half-dozen 8100s and all of them worked fine. GeForce video cards are more forgiving than the Radeon 7500s, but there's no real difference on stuff that old. (Shameless self-promotion: You can get it running on stuff that is [MUCH older]("http://www.ubuntuforums.org/showthread.php?t=294292"). :D )
-->Thanks, I'm glad to hear that you've had luck with 8100s; 

If you have the 1600x1200 screen, you'll want at least the 32Mb GeForce2 video card. The 16Mb card has slow redraw rates at that resolution. Luckily, those cards run about $20 on ebay. A full-fledged 64Mb GeForce4 Go 440 MX is closer to $100, but worth it. I have one in my 8000 and love it.
-->With a little more investigation, I was able to find the video specs for my 8100; they are:
-NVIDIA GeoForce2
-Screen Resolution 1400x1050 pixels
-Color Quality is "Highest (32bit)"

And if you've got an extra $60 to spare, you can dump the full 512Mb of PC133 in those, and it's golden. If I remember right, the 8100 can hold processors up to 2Ghz+, and that means your machine is far from obsolete.
-->I'm not sure what you're getting at exactly here; this is a little bit over my head technically speaking, but thanks anyway :)

I've not worked with the MiniPCI wirless card; I use a WPC11 v3 -- it's a b-wireless card, but needs no configuration aside from the WEP key.

Have fun! You're going to love it!
-->Thanks, I'm really looking forward to trying Ubuntu!

---

### Post by K.Mandla on 2006-11-08
> **SurferKauai said:**
> With a little more investigation, I was able to find the video specs for my 8100; they are:
-NVIDIA GeoForce2
-Screen Resolution 1400x1050 pixels
-Color Quality is "Highest (32bit)"
That's decent. See if you can find out how much video RAM the card has. It should show up in the BIOS configuration. No matter how much memory it has, those were very good graphics cards. It'll work perfectly in Ubuntu.

> **SurferKauai said:**
> I'm not sure what you're getting at exactly here; this is a little bit over my head technically speaking, but thanks anyway
My point was just that, should you ever feel it's not moving as fast as you like, you can add more memory to it and find a faster processor. 

The 8000-series peaked at 1Ghz; processors faster than that won't fit on the motherboard. On the other hand, the 8100s and 8200s used a different shape processor that reached 2Ghz and faster ... if I remember right. ;-)

---

### Post by SurferKauai on 2006-11-09
Thanks very much for that clarification.

---

