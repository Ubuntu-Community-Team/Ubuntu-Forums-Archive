---
title: "Hey all! Messing with Jaunty for the fun of it, FGLRX issues"
date: 2009-02-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by pyrokenx on 2009-02-18
just wanted to check in with anyone playing around with jaunty, has anyone gotten fglrx to work correctly on it on HD Radeons (e.g. 2xxx series and up?)..

Keep in mind I dont expect things to magically work for me given I am using pre-release software, just wanted to see if anyone has had any luck

Thanks alot!

---

### Post by DougieFresh4U on 2009-02-18
Can't help but if it makes you feel better my upgrade failed on my AMD machine with ATI 3200, "fglrx issues" were very present during upgrade and fglrx worked excellent with Intrepid. No problems on my Intel machine. It's a known issue with Jaunty.

---

### Post by rbmorse on 2009-02-18
FGLRX doesn't work with the pre-release version of Xserver (1.6) that comes with Jaunty. Yet. The same thing happened during Intrepid's development. At some point the appropriate accommodation will be made to get FGLRX working, but don't expect it until after either Jaunty or Xsever 1.6 have gone final. 

Jaunty should load the radeon driver by default if it properly detects your card. The 1XXX HD Radeon cards should be fully functional. Owners of the 2XXX, 3XXX and 4XXX Radeons should get excellent 2D performance, but hardware accelerated video and 3D are still cooking.

---

### Post by jerrylamos on 2009-02-18
From the Alpha 4 announcement:

A new XServer, version 1.6, is included in Alpha 4. The binary proprietary fglrx driver is not yet supported for this server and will exhibit various serious issues if run against it. Users of this driver are encouraged to wait or to switch to the open source -ati driver in the meantime. Launchpad Bug #308410

Not sure if this is relevant...

Jerry

---

### Post by bcat on 2009-02-18
Sorry if this is a stupid question, but is Compiz supposed to work with the radeon driver? I thought so, but attempting to enable desktop effects gives an error. Does it not do the necessary video acceleration magic?

---

### Post by pyrokenx on 2009-02-19
> **bcat said:**
> Sorry if this is a stupid question, but is Compiz supposed to work with the radeon driver? I thought so, but attempting to enable desktop effects gives an error. Does it not do the necessary video acceleration magic?


depends on the ati card.. if its newer than Radeon 9200 then you need fglrx

also there are various cards before the 9xxx series that only work with fglrx for some reason

ATI on Linux has always been to a slight degree a bag of hurt, however seems to improve slowly all the time now..  I hope the RadeonHD driver catches up to ATI's proprietary driver soon

---

### Post by sloggerkhan on 2009-02-19
It's not as simple as last poster makes it out to be. With open ati driver I know most x series (x700, x800 gen) will work with compiz and have okay 3-D with open driver.

---

### Post by pyrokenx on 2009-02-19
> **sloggerkhan said:**
> It's not as simple as last poster makes it out to be. With open ati driver I know most x series (x700, x800 gen) will work with compiz and have okay 3-D with open driver.

Ah thankyou, I must be running on outdated info :)

---

### Post by Yashiro on 2009-02-19
Radeon 4850 here. It's not recognised at all by xorg and thus is stuck using the default vesa driver.

Fglrx, as mentioned above, does not work either.

---

### Post by yodermk on 2009-02-20
> **Yashiro said:**
> Radeon 4850 here. It's not recognised at all by xorg and thus is stuck using the default vesa driver.

Fglrx, as mentioned above, does not work either.

Same here with an HD 3200. Every screen update, such as Firefox scrolling a page, is *painful*.

I notice it did not load the drm and radeon kernel modules, but when I modprobed them and restarted X, nothing changed.

xorg.conf does not specify the radeon driver. Maybe I'll try adding it.

If I could fix this, I'd be pretty happy with Jaunty. :)

---

### Post by Kazade on 2009-02-20
> **yodermk said:**
> Same here with an HD 3200. Every screen update, such as Firefox scrolling a page, is *painful*.

I notice it did not load the drm and radeon kernel modules, but when I modprobed them and restarted X, nothing changed.

xorg.conf does not specify the radeon driver. Maybe I'll try adding it.

If I could fix this, I'd be pretty happy with Jaunty. :)

I have an HD3200, it's not supported by the xserver-xorg-ati driver with any kind of acceleration (2D or otherwise) which is why it is slow. However, the r6xx-r7xx branch of the radeonhd driver does have experimental 2D acceleration support for your card. If you fancy a challenge, head over to #radeonhd on Freenode and ask for some help. There is a bash script lying around which will checkout and install the latest drivers from the repository.

In the end I went back to Intrepid on that machine, at the time (about 3 weeks ago) acceleration worked but there was loads of corruption, however I think they have fixed that now.

---

### Post by pyrokenx on 2009-02-23
so I just downloaded catalyst 9.2, I wanted to let everyone know that I still get the exact same issue.  Anyone else have better results? let me know.

---

