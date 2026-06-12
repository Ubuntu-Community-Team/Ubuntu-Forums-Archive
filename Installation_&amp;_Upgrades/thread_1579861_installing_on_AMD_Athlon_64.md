---
title: "installing on AMD Athlon 64"
date: 2010-09-22
forum: Installation &amp; Upgrades
---

### Post by scukrainian on 2010-09-22
I am trying to install ubuntu on my home PC which is running an AMD athlon 64 with 1 gig of RAM.  When I try to boot off the CD the screen goes black and then the computer shuts off the monitor.  So I tried again and I hit the tab key when booting to get to the first options screen and enter the kernels:  mem=512 fb=false no-hlt vga=771.  When I hit enter, the screen goes black and never comes back up.  Got any other ideas?

---

### Post by coffeecat on 2010-09-22
> **scukrainian said:**
> I am trying to install ubuntu on my home PC which is running an AMD athlon 64 with 1 gig of RAM.  When I try to boot off the CD the screen goes black and then the computer shuts off the monitor.  So I tried again and I hit the tab key when booting to get to the first options screen and enter the kernels:  mem=512 fb=false no-hlt vga=771.  When I hit enter, the screen goes black and never comes back up.  Got any other ideas?

What graphics card do you have? There may be a problem with that.

Also, did you check the md5sum of the downloaded ISO and did you burn the CD at a low speed? Which version of Ubuntu is the live CD?

---

### Post by scukrainian on 2010-09-22
The card I have in right now is an Asus  EAH 3450 but I tried to load it with the on board Nvidia graphics and had the same problem.  As far as the disk goes, I tried two different disks one of which loaded on my laptop and the live version on my work PC.[B][B][B]  I don't know what speed it burned at, but it is the latest version 10.04.
[/B]

[/B][/B]

---

### Post by coffeecat on 2010-09-22
OK, that gives us a little more to work on. The fact that neither an ATI card (the ASUS) and your onboard nvidia graphics will work, and that the disc boots on another machine suggests that the problem is with the BIOS. I'm afraid some BIOS's are buggy and Linux-hostile. What's the motherboard? Googling for the motherboard + Ubuntu might bring up something useful.

The only other thing I can suggest is to try some of the other boot options on this page:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Sometimes acpi=off helps.

---

