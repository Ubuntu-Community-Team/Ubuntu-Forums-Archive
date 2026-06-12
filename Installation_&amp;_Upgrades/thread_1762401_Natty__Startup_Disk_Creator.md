---
title: "Natty:  Startup Disk Creator"
date: 2011-05-19
forum: Installation &amp; Upgrades
---

### Post by coljohnhannibalsmith on 2011-05-19
Hello,

I've recently created a Boot Image of Natty on my 4GB flash-drive with Startup Disk Creator; and enabled "**Boot From USB KEY"** in the BIOS; and changed the boot device order to list this device first; and my system apparently can't read it...

Comments please...




Thanks, Hannibal

---

### Post by djzsolti on 2011-05-19
Garfikus kártya probléma ATI Radeon HD 6870 es kártya nem meg felelöen müködik kérem segitsenek nekem mitt tegyek E-mail : [EMAIL="djzsolti@freemai.hu"]djzsolti@freemai.hu[/EMAIL]

---

### Post by jre6 on 2011-05-19
Maybe you should try doing this with Unetbootin?

---

### Post by coljohnhannibalsmith on 2011-05-19
> **jre6 said:**
> Maybe you should try doing this with Unetbootin?

Thank you,

It's a very nice tool; and a necessary one; as Startup Disk Creator will only allow creating an Ubuntu-distro startup drive, not even Clonezilla or Linux Rescue CD images are permitted.

Anyway, I think I've got this sorted out...  I had selected ***USB Key*** as the boot-device; and apparently my BIOS saw this as a ***USB HDD*** instead, since it's => 2GB.  Also, my 1 GB flash-drive 'is' seen as a USB Key.  So in order to use both of them, I had to set the boot-device order as follows, in my BIOS:

USB Key
USB HDD
USB CD ROM
Slimtype - XXXXXXXXXX (internal CD/DVD device)
PATA HDD - XXXXXXXXXX (internal HDD)
etc.

[COLOR=Blue]***Now both devices & both Startup CD Creator & Unetbootin work as advertised...***[/COLOR]

[IMG]http://www.seanographic.com/portfolio/portfolio/it-works-logo.jpg[/IMG]




[B]
Thanks Hannibal[/B]

---

### Post by coljohnhannibalsmith on 2011-05-19
> **djzsolti said:**
> Garfikus kártya probléma ATI Radeon HD 6870 es kártya nem meg felelöen müködik kérem segitsenek nekem mitt tegyek E-mail : [EMAIL="djzsolti@freemai.hu"]djzsolti@freemai.hu[/EMAIL]

[COLOR=Blue]***He looks lost...***[/COLOR]

---

