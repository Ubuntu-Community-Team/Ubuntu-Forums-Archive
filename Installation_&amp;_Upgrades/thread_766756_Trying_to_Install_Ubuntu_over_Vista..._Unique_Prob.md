---
title: "Trying to Install Ubuntu over Vista... Unique Problem"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by cmlewin on 2008-04-25
Hey All-
I decided to be an imbecile and borrowed a friends copy of Vista Ultimate a few weeks ago to install it as an Upgrade over XP on my comp. Problem is it was for his DELL laptop and not for my HP machine.  As a result I had lost a lot of CD drive functionality and now it is not recogizing I have a CD drive at all.  I also cannot install the HP drivers because it thinks I'm on a Dell so I do 'not meet minimum system requirements'. B/C of this it seems I cannot boot from an ubuntu disc I created using the new Hardy Heron .iso.  Is there a way to mount the .iso on a partition and boot from there... Or can I install Wubi and then install a complete download from there... Or is the Vista boot sequence as such that it doesn't want to let me boot from the disc (in boot menu it still reads that I have a disc as an option but boots straight into Vista still.  What to do?

Thanks!

---

### Post by IgnorantGuru on 2009-11-01
BIOS controls your CD booting - shouldn't be affected by the OS on the hard drive.  Check your BIOS boot settings to make sure the CD drive is first in the boot sequence.  (Press Del or F1 or whatever to get into the BIOS at boot.)

Barring that, I would try installing from a USB stick made with unetbootin.

---

### Post by IgnorantGuru on 2009-11-01
Also, make sure your install CD is a good burn - maybe it's just not bootable.

---

