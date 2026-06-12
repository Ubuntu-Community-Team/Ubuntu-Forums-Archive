---
title: "Reinstall windows XP !!!! with or over non partitioned Lubuntu"
date: 2020-10-12
forum: Installation &amp; Upgrades
---

### Post by adamdylan on 2020-10-12
Hi installed lubuntu 18.04   in old Asus eee pc  (only 32 bit pc so had to inst 18.04) I could only install full ie no partition of windows.

How do I reinstall windows xp?  (I want a seperate instalation of xp as pc only has 1 meg ram) 

I have tried via windows to create a ubuntu iso boot disc but the pc will not recognise it ? 

I think this is because pc now has a fully  linux formatted hard drive and when I try to make a a boot disc in iso to usb or universal usb installer formatted fat32 or ntfs it does not recognise

Any ideas guys? thanks   Adam

---

### Post by CelticWarrior on 2020-10-12
Welcome.

Countless time it has been explained that the ability or lack of it to boot installation media has nothing to do with the already installed OS if any. The problem is ALWAYS the media itself and/or the firmware (Bios or UEFI - obviously BIOS in your case - settings and/or (quite frequently) user's inability to press the correct key on time.

Now, a few additional comments:
[LIST=1]
[*]32-bit hardware is *de facto* obsolete at the time of this writing. Very few options remain for still supported OSes which brings us to #2...
[*]Lubuntu 18.04 as with any other Ubuntu flavors has only 3 years of support instead of the 5 years the standard Ubuntu gets; this means your release is supported until **April 2021** only and knowing that one is the last Ubuntu based 32-bit release at said date it's game over.
[*]Of the few remaining options with some more "shelf life" I would recommend AntiX or Debian. Again, Ubuntu or flavors aren't no longer an option for 32-bit hardware.
[*]**Windows XP has NO SECURITY UPDATES since 2014!** It shouldn't be used connected to the internet, period. And the truth may hurt but knowing it may save you from yourself in the long run: If you're asking this kind of questions you **DEFINITELY **shouldn't be even thinking about using such an obsolete OS, it's dangerous for your own personal data and it takes only seconds on the internet for it to be used as part of an attack that will ultimately hurt others.
[/LIST]

---

### Post by ajgreeny on 2020-10-12
As CW says, do not connect XP to the internet; it's far too dangerous.
I have similar spec netbook with 1G ram and Atom 270N CPU which is still usable with Debian 10 Testing, and openbox as the low resource Window Manager. It is OK for web browsing, email and documents, but I avoid video except for some low resolution stuff, ànd use Abiword and Gnumeric for office documents as libreoffice is far too big and slow.

---

### Post by TheFu on 2020-10-12
To install winxp, get out the winxp disks that came with the Eee.  If you don't have those, nobody can help. Please don't use XP on any network that  isn't air-gapped from other networks. 

If you want a dual-boot setup, winxp needs to be installed first. Be certain to thank msft for that.

I had one of those Eee w/ 2GB and loved it. Ran xubuntu or lubuntu (lxde) on it. If the problem is that Lubuntu (lxqt) is too bloated, then use a very light distro like tinycore.  Tinycode runs in 64MB of RAM. It will fly on any Eee model.

---

### Post by guiverc on 2020-10-12
I use an
```

asus eepc 1000HE (intel atom n270, 1gb, intel mobile 945gse integrated), wireless RT2790
```

in testing x86/32-bit ISOs, including Lubuntu (*last being 18.04.5 August 2020, but it was also used to test 18.10 & 19.04 ISOs in the past*)

As others have said, the installation of Lubuntu won't impact the ability to install another OS, including windows XP.  Maybe your issue is just getting a thumb-drive to boot?

It's wasn't a favorite testing device for me, as whilst it's BIOS will happily boot DVD/CDs, I use thumb-drives and mine does **not** automatically boot a thumb-drive and must be specifically told to boot it.  That has nothing to do with the OS on the hdd, but it's the firmware supplied by *asus*.  This maybe your issue (*if you're trying to boot a thumb-drive, you need to force it to boot it*..)

---

