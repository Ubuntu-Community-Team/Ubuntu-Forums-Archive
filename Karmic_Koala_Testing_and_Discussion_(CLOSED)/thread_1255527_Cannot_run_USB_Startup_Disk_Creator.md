---
title: "Cannot run USB Startup Disk Creator"
date: 2009-09-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by GeorgeVita on 2009-09-01
**[COLOR="Blue"]NEW EDIT:[/COLOR]** **USB Startup Disk Creator 'freezes' when selecting persistent file > 4GB**
... Please see post#10

**EDIT:** First problem solved after last update:> [https://bugs.launchpad.net/bugs/422671](https://bugs.launchpad.net/bugs/422671)
This bug was fixed in the package usb-creator - 0.2.5

*******

Hi,
I am usually testing all 9.10 Alphas with a clean installation from a LiveUSB stick.

My procedure is: Boot 9.04, System > Administration > USB Startup Disk Creator point to the 9.10 AlphaX .iso and use as target a USB stick which is unmounted and pre-formatted to fat32 from GParted. Then boot from the 9.10 LiveUSB and 'install Ubuntu'...

I tried to use USB Startup Disk Creator from my running 9.10 Alpha4 + updates and the following error occurred:

```
An unhandled exception occurred:
Duplicate object id 'alignment3' on line 630 (previously on line 287)
``` just after entering my password ('starting administration...'). If the password is already given (by other gksu) the error appears immediately.

I need your opinion/help to determine what is it:
- too soon to have the 'USB Startup Disk Creator' working?
- a fault in my system?
- a bug?

**Thanks** in advance,
George

---

### Post by xens on 2009-09-01
Hi!

working for me, I saw an update today form this package, can you try sudo apt-get updat && sudo apt-get dist-upgrade ?

---

### Post by laborg on 2009-09-01
i tried it before and after the update with no success. usb-creator is quite a mess at the moment...

---

### Post by ViRMiN on 2009-09-01
Try this, [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) it's in the repo's.  I use it to create bootable USB sticks for my netbook.

---

### Post by GeorgeVita on 2009-09-01
... after latest updates the initial problem (An unhandled exception occurred...) did not happened.
Trying to use 'USB Startup Disk Creator' stucked after selecting the .iso, apport worked and a bug already exists: 
[https://bugs.launchpad.net/bugs/421373](https://bugs.launchpad.net/bugs/421373) and 'affects me'.

G

---

### Post by miegiel on 2009-09-02
> **GeorgeVita said:**
> ... after latest updates the initial problem (An unhandled exception occurred...) did not happened.
Trying to use 'USB Startup Disk Creator' stucked after selecting the .iso, apport worked and a bug already exists: 
[https://bugs.launchpad.net/bugs/421373](https://bugs.launchpad.net/bugs/421373) and 'affects me'.

G

[https://bugs.launchpad.net/ubuntu/karmic/+source/usb-creator/+bug/422671](https://bugs.launchpad.net/ubuntu/karmic/+source/usb-creator/+bug/422671) is bugging me :) Confirmed + High

---

### Post by komputes on 2009-09-02
I just did a roundup of 5 duplicate bugs against usb-creator in karmic.

Here is the master bug: [https://bugs.launchpad.net/ubuntu/karmic/+source/usb-creator/+bug/422671](https://bugs.launchpad.net/ubuntu/karmic/+source/usb-creator/+bug/422671)

---

### Post by keypox on 2009-09-03
works sometimes sometimes it doesnt... dunno why.

---

### Post by GeorgeVita on 2009-09-09
Solved after last update:> [https://bugs.launchpad.net/bugs/422671](https://bugs.launchpad.net/bugs/422671)
This bug was fixed in the package usb-creator - 0.2.5

Tested also creating a persistent 1GB area and works fine (updated, new packages installed, save to desktop, etc) like an installation.

G

---

### Post by GeorgeVita on 2009-09-12
**[COLOR="Blue"]New tests needed![/COLOR]**
**USB Startup Disk Creator 'freezes' when selecting persistent file > 4GB**

Working with various liveUSB sticks, I tried to make some 'persistent' using only Ubuntu 9.10 standard tools. I manage it with the following procedure, but during the tests I realize a 'freeze' of the program when trying to make a very large (6.2GB) persistent file.

I am not sure if this was a problem from my USB stick or the fat file system or a 'bug'.

Please post any technical idea or better spend a half of an hour to test it.

My procedure:
- Backup previous data from the 'target USB stick' (8GB minimum)
- Boot 9.10, attach 'target USB stick', wait for its' icon to appear
- right click 'target USB stick' icon and select 'Format'
- follow instructions and format it to 'Fat' (default), place a 'name'
- after formating, close the [TWO]("http://ubuntuforums.org/showthread.php?t=1262133") 'file managers' appeared
- from System > Administration > USB startup disk creator
- point to the 'target .iso file'
- point to the 'target USB stick'
- adjust persistent file LARGER than 4GB
- start installation and wait ... (over 20 minutes for 5GB)
- finally press 'quit'
- REMOVE 'target USB stick', shut down and TRY it!

Thanks in advance,
George

---

