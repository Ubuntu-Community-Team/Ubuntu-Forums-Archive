---
title: "Installing over windows7 pro"
date: 2011-12-24
forum: Installation &amp; Upgrades
---

### Post by koler1952 on 2011-12-24
Goodmorning to all, I'm an old guy half new user in that I've been using Ubuntu for some time installed directly onto a virgin hd without problems but the other day I bought a Acer aspire desktop M1641 with Windows7 pro demo installed which doesn't interest me at all.
 
PROBLEM: How to write over windows7 pro with Ubuntu. All attempts just putting Ubuntu in the DVD tray doesn't work. I've come to the conclusion I have to format the HD before with the necessary the necessary "extensions" (Not Fat 32 etc) so I've down load "Gparted live" but still am unable to use it. Any help/tips would be greatly appreciated
 
Christmas wishes and so on
koler1952

---

### Post by darkod on 2011-12-24
You shouldn't need to prepare anything in advance. It can install over win7 during the installation.

It sounds like it's not booting from the DVD device. Can you enter BIOS and confirm CD-ROM is before HDD in the boot devices?

Alternatively, during boot up there is usually a key you can press to enter Boot Menu. On different computers it's different, it might be F12, or F10, etc. This will bring up a boot menu and you can select to boot from CD-ROM, without going into bios and making changes.

---

### Post by koler1952 on 2011-12-24
Thanks for the reply...this is what I've been doing, going into boot and booting from DVD reader but it gets "stuck".  Only Puppy linux gets me to its desktop but then mouse and keyboard don't work. If I can wipe out Windows/ completely maybe is the best solution.
Koler1952

---

### Post by fantab on 2011-12-24
> **koler1952 said:**
> Thanks for the reply...this is what I've been doing, going into boot and booting from DVD reader but it gets "stuck".  Only Puppy linux gets me to its desktop but then mouse and keyboard don't work. If I can wipe out Windows/ completely maybe is the best solution.
Koler1952

The Ubuntu .iso could be corrupt... you can check that or download again. If you haven't then burn the .iso at the slowest possible speed.

And if DVD is not working try USB. 

Does Gparted live boot?

---

### Post by koler1952 on 2011-12-26
Still struggling...the iso files are ok. There's surely something simple I don't understand. Disconected the HD and tried to upload Puppy linux (which can run only on the RAM) and arrives to the Puppy Desktop but mouse and keyboard don't work. Likewise other linux OS's that should run live from CD/DVD don't

---

### Post by West201 on 2011-12-26
Why don't you install another version of ubuntu such as 10.10 or 11.04 and then upgrade to 11.10 ? 

I've had use this method a few times.

---

### Post by mörgæs on 2011-12-26
As mentioned above, booting from USB is worth trying. In general it is safer than using CD/DVD.

---

