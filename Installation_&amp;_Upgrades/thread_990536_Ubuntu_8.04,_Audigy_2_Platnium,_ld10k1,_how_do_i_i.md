---
title: "Ubuntu 8.04, Audigy 2 Platnium, ld10k1, how do i install this driver?"
date: 2008-11-22
forum: Installation &amp; Upgrades
---

### Post by dv-design on 2008-11-22
Hello,

Im having issues with my sound card. Currently i have no sound, not even feedback.

I have a Soundblaster Audigy 2 platnium, and with some pokeing around found what i beleive to be the right driver. It came as a compressed folder, and im having trouble figureing out exactly how i install it.

ld10k1-0.1.8 is the name of the folder/driver.

The install file has directions but they are very fuzzy.

> unpack source
run ./configure --prefix=/usr
run make
run make install

then run 
  ld10k1 -d
or 
  /usr/sbin/ld10k1 -d
as root
and run init script
  init_audigy
for audigy soundcard
  init_live
for sb live soundcard

If this makes sense to anyone please help, im at a lose and wish i had sound.

---

