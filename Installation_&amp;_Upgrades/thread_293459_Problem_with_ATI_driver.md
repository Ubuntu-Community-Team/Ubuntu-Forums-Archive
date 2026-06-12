---
title: "Problem with ATI driver"
date: 2006-11-05
forum: Installation &amp; Upgrades
---

### Post by clapton on 2006-11-05
I've install the edgy ubuntu and I've got some problems.

Always when I install the ati driver, with method 1 or 2 from wiki guide,I can't see anything, my X server doesn't start and I can't change screen with ctrl+alt+f2 and I can't kill with ctrl+atl+backspace .

My Ati card is an 9550 256 Mb.

Seems to me that I've got to change to dapper again...

---

### Post by spandon on 2006-11-05
Hi Clapton,
I had a problem with a Edgy live CD and install with a machine using an ATi card.
The way I got out of it, using Live cd was :
Having rebooted with disk in, when the first screen apears Load Install etc, press Escape the add the following command line:
**boot: vga 771 napic nolapic**
Try it with your live cd, if you get the same result as I did (rtes of 1280 x 1024) the you know your system is compatible with Edgy (Dapper worked without any probs  - but with a quite low res).
I used the Alternative cd to install edgy, using the following command line at start:
**install vga 771 napic nolapic**
The result was the same as the Live cd.
Hope it works for you - only takes a couple of mins to test.
Don

---

### Post by clapton on 2006-11-05
my problem is "after install"
After install edgy, I install ati driver and I can't use anymore :\
For me, it's very important have 3D driver install because of refresh rate

---

### Post by PosTi85 on 2006-11-21
ATI drivers sucks for 9550 on edgy

---

### Post by rjpiercy2 on 2006-11-21
I had problems with my ATI driver.  I was able to solve them using this guide.

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

I have a Radeon 9200 SE, which required that I recompile the driver according to this.

[https://help.ubuntu.com/community/Radeon_9200/9250_%28RV280%29_and_DVI](https://help.ubuntu.com/community/Radeon_9200/9250_%28RV280%29_and_DVI)

Hope this helps.  Good Luck!

---

