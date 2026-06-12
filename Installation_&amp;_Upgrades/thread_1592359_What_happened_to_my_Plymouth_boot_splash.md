---
title: "What happened to my Plymouth boot splash ?"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by insaini on 2010-10-10
I just finished upgrading and for the most part went smoothly..

before the upgrade I was running Lucid.. had some ppa's setup like xorg edgers but purged that ppa and the upgrade to maverick was dandy..

however before the upgrade my plymouth solar theme would load up on startup and shutdown beautifully.. at a gorgeous 1680x1050 resolution..

im using nvidia proprietary drivers.. (was before and I am now after the upgrade) 

however now.. I only get a text splash or sorts.. it just says Ubuntu 10.10 and has 4 dots that alternate between orange and white.. wtf??

does anyone have any insight to this?  ive tried update alternatives to no avail.. and ive googled.. something about adding a FRAMEBUFFER=y line to the splash conf.d file for initramfs but that didnt do anything either..

im at a loss to explain.. is there any logs for plymouth ?

---

### Post by mörgæs on 2010-10-10
How does the boot sequence look when booted from a live CD?

---

### Post by insaini on 2010-10-10
> **mörgæs said:**
> How does the boot sequence look when booted from a live CD?

Actually I just solved this.. never booted from a live cd.. only did the upgrade.. never downloaded the full iso

[http://www.webupd8.org/2010/03/how-to-get-plymouth-working-with-nvidia.html](http://www.webupd8.org/2010/03/how-to-get-plymouth-working-with-nvidia.html)

the fix was a simple one liner..followed the webupd8 link exactly.. funny and stupid thing is.. I now totally remember doing this for my lucid upgrade.. :|

---

