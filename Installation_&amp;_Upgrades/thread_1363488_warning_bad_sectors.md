---
title: "warning: bad sectors"
date: 2009-12-24
forum: Installation &amp; Upgrades
---

### Post by Orion_PKFD on 2009-12-24
Hi all,

After installing ubuntu in a laptop with Vista (dual boot) something strange happened. After the instalation and everytime it starts a message appears and it's something like this:

Your hard drive may have health problems and an icon appears on the top of the screen and says in one part that the disk has many bad sectors.

Why this happened? I did something wrong in the instalation process or it is a problem that has already occured before the instalation.

Best regards and merry christmas

---

### Post by mzaiemo on 2009-12-24
hi,
the error popup while boot in windows or in ubuntu?

---

### Post by lncoll on 2009-12-24
> **Orion_PKFD said:**
> Hi all,

After installing ubuntu in a laptop with Vista (dual boot) something strange happened. After the instalation and everytime it starts a message appears and it's something like this:

Your hard drive may have health problems and an icon appears on the top of the screen and says in one part that the disk has many bad sectors.

Why this happened? I did something wrong in the instalation process or it is a problem that has already occured before the instalation.

Best regards and merry christmas

You did all ok, but your hard disk is in trouble.
Most of all new hard disks have a function called SMART, this function reports all data about HD status, included how many bad sectors there are in the HD.
In Windows there is not any utility installed by default to test this data, now in 9.10 a utility is installer and loaded by default, this is the reason you have this bad news.

Recommendations:
- Back up all your important data ASAP.
- Earn some money and buy a new HD :P

P.D. An HD with bad sectors can work for years without problems or can crash in some hours.

---

### Post by ctrobbia on 2009-12-25
I am having this too. This is a brand new (like yesterday old) netbook to which I installed Windows 7 first, then Ubuntu Netbook Remix. As soon as I boot into Ubuntu it says harddisk has bad sectors.

chkdsk in windows shows nothing on the windows partition.
check badblocks and ran fsck on linux partition
for grins ran Spinrite (which has never failed me in the last 5 years I've used it) with no problems found.
Just in case everything was wrong I ran manufacturer (drive) test. No errors.
And since it is a brand new netbook and I would enjoy calling tech support on Christmas I ran dell diagnostics (in case it came up with something and I really did need a new drive) no errors/problems.

Any advice- since I am not sure what situation the OP is but maybe they are in a similar situation (though 9 times out of ten it is a bad drive) and any advice would help.

Many regards and Merry Christmas.

---

### Post by Orion_PKFD on 2009-12-26
> **mzaiemo said:**
> hi,
the error popup while boot in windows or in ubuntu?

It pops up on ubuntu only and pops every time and the icon is always there.

Because of that I'm afraid to instal on my brand new laptop :(

Another thing: why apt-get doesn't work right from tha start? I have to do something first to get this working?

Thank you all

---

### Post by Orion_PKFD on 2009-12-26
Should I change SWAP when installing? It created only a few MB...

---

