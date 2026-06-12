---
title: "getting xubuntu running on some really old hardware"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by whybuybeta on 2007-12-05
7.10 was a massive failure on this old thinkpad 390 for some reason, where dapper has been installed with not much problem in the past. this thing has something like a PII 233 mhz and 160 mb ram with about 3gb of hd space, should be more than enough for the text install which I used to get dapper on there before. the biggest problems I haven't been able to get around so far:

- pcmcia seems to start ok and the slot nic is active but the install doesn't detect it, atheros/wg511t
- base system install halts around 60% every time from some unknown error
- hd is detected as scsi instead of ide for some reason, I don't know if this is related but partitioning sees the entire drive and doesn't give any errors

I've tried adding various combinations of these switches to the install command line that got me through the last time I had dapper working - noapic, nolapic, acpi=off, pci=noacpi, pnpbios=off

I figure the pnpbios switch could prevent the pc card nic from getting detected, I've tried this with and without but when I don't use it I get a pnpbios error unrecognized at 0x82.

anybody get gutsy working on some old ibm stuff?

---

### Post by kerry_s on 2007-12-05
the *ubuntu's are not the best for the old stuff, ubuntu drops support for the older stuff, that it doesn't think ubuntu would be run on. your best bet would be to drop down to a older version or better yet go straight debian, you can also try the varies mini distro's that are made for those kind of spec's.

find all kinds of distro's here-> [http://distrowatch.com/](http://distrowatch.com/)

i recommend debian-> [http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso)

debian net installer-> [http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-businesscard.iso)

for those specs, you can get reasonable performance with a debian base install, then just adding what you need.

---

### Post by Pumalite on 2007-12-05
[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)
If it doesn't work, try DSL or Puppy.

---

### Post by aldenhg on 2007-12-05
I second a vote for DSL (Damn Small Linux). It's tiny and it'll run on a dead badger. Provided the dead badger's CPU is supported, of course.

---

### Post by whybuybeta on 2007-12-06
is there a huge difference between xubuntu server install and straight debian if I'm going to use xfce anyways? I stuck with it since 6.06 was easy to get up and running, including the wireless card (wpa is a completely different story though). dsl and puppy looked like barebones overkill to me since the dapper xfce package was definitely snappy enough as it was. as of now dsl doesn't even have pcmcia support so getting my nic working would be a complete pita.

---

