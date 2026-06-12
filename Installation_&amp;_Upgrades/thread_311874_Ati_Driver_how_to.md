---
title: "Ati Driver how to"
date: 2006-12-03
forum: Installation &amp; Upgrades
---

### Post by pgt on 2006-12-03
as many im a linux beginner so bear with me

I tried upgrading to dapper from breeze buti get stuck on a black screen, so imhoping mmy display dirvers will fix it...

How do I go about installing ati radeon 9800xt drivers on ubuntu 5.10?

Thanks!

---

### Post by u0014 on 2006-12-03
> **pgt said:**
> as many im a linux beginner so bear with me

I tried upgrading to dapper from breeze buti get stuck on a black screen, so imhoping mmy display dirvers will fix it...

How do I go about installing ati radeon 9800xt drivers on ubuntu 5.10?

Thanks!
**** for the longest time i had a problem with my ati card not getting its drivers properly installed, I have a ab ATI X800 XT. I am new to linux so I can't explain how this happens but it appears [in my case] if you install an nvidia card [or better yet install ubuntu with the nvidia card in] and get it to work right (driver with 3d rendering) then take out that card and put an ATI 9800 or higher card and install the ati driver ([http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)) you will get your ati driver running and with 3d rendering. I have tried this a few times and it has worked everytime for me. I ran Quake 4 with it no lags.
I hope this works for you.

---

### Post by u0014 on 2006-12-03
for video configuration use command:
dpkg-reconfigure xserver-xorg

it help you reconfugure your x server confuiguration

---

### Post by Sprite1990 on 2006-12-03
Try [http://albertomilone.com/driver_edgy.html](http://albertomilone.com/driver_edgy.html)

For ATI drivers, it worked for me (although I followed the instructions to install Nvidia Drivers)

---

