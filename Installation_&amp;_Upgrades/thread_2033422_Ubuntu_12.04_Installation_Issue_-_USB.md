---
title: "Ubuntu 12.04 Installation Issue - USB"
date: 2012-07-26
forum: Installation &amp; Upgrades
---

### Post by Furler on 2012-07-26
I'm trying to install the latest Ubuntu but I am not having much luck. When I try using PendriveLinux it will get stuck on:

SYSLINUX 4.04 EDD 2011-04-18 Copyright (C) 1994-2011 H. Peter Anvin et al 

If I try to use Unetbootin, I get stuck on:

Verifying DMI pool data...

I've tried two different USB drives.

Any suggestions?

---

### Post by kun4L on 2012-07-26
Is the first boot device properly set ?
and it might be that the usb drive is not getting mount..

---

### Post by Furler on 2012-07-26
Yes, I went into the BIOS and told it to boot from USB-HDD first. If it wasn't getting mounted would I still be getting the SYSLINUX hang?

---

### Post by ajgreeny on 2012-07-26
Did you check you .iso file with the ubuntu hashes to make sure it is a good image?
[UbuntuHashes - MD5sum]("https://help.ubuntu.com/community/UbuntuHashes")

---

### Post by Furler on 2012-07-26
I can't say that I have checked that but I have downloaded it twice on my Windows PC and then tried downloading it on an old Linux Mint machine, all of them gave the same result.

---

### Post by RezPix on 2012-07-26
You could try downloading a MD5 Hash Checker.

The MD5 hash's are available here [https://help.ubuntu.com/community/UbuntuHashes/](https://help.ubuntu.com/community/UbuntuHashes/)
Might be worth a try.

---

