---
title: "Can't boot from CDROM"
date: 2005-04-11
forum: Installation &amp; Upgrades
---

### Post by jabowery on 2005-04-11
I'm installing Ubuntu on an old laptop for a friend but BIOS isn't booting from CDROM.

Searching the Wiki for "floppy" doesn't show a howto for what he needs to do:

Boot from a startup install floppy that can further read the CDROM for everything else.

---

### Post by jordanau on 2005-04-11
[QUOTE=jabowery]I'm installing Ubuntu on an old laptop for a friend but BIOS isn't booting from CDROM.

Searching the Wiki for "floppy" doesn't show a howto for what he needs to do:

Boot from a startup install floppy that can further read the CDROM for everything else.[/QUOTE]
 have you changed your boot order in the bios? or are you saying the laptop is too old to do that?

---

### Post by jabowery on 2005-04-11
[QUOTE=jordanau]have you changed your boot order in the bios? or are you saying the laptop is too old to do that?[/QUOTE]

Well, for what the information is worth:

The BIOS says it supports booting from CDROM but when the BIOS is set to boot from CDROM it never finds the boot image on the CDROM.  I've tried several different bootable CDROMs in the device.... everything from Windows to Fedora to Maxtor diagnostics CD -- all of which are supposed to be bootable.

PS: Yes it does boot from floppy and yes it does read from the CDROM when an OS is installed but there is no OS installed now so the install must be from boot media.

---

### Post by joe_williams on 2005-04-11
I haven't looked at this...but perhaps it will help:
[http://www.ubuntulinux.org/wiki/SmartBootManagerHowto](http://www.ubuntulinux.org/wiki/SmartBootManagerHowto)

---

### Post by jabowery on 2005-04-13
[QUOTE=joe_williams]I haven't looked at this...but perhaps it will help:
[http://www.ubuntulinux.org/wiki/SmartBootManagerHowto](http://www.ubuntulinux.org/wiki/SmartBootManagerHowto)[/QUOTE]

That does the job.  

Thanks!

---

