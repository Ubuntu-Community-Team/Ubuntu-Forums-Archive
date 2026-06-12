---
title: "Edgy PXE Keyboard Selection Automation"
date: 2007-03-15
forum: Installation &amp; Upgrades
---

### Post by eonnen on 2007-03-15
Hello,

I'm grappling with one last issue in my Automatic PXE installation of Edgy servers - keyboard selection. I started by following the installation guide and sample append options for the PXE configuration file, then tried some other examples from google searches, and finally went to the source but am still stuck. At this point I believe the answer is probably quite simple, but it's eluding me.

I believe the source of the problem is in the kbd-chooser kernel parameter as my installation *always* makes me perform the keyboard identification. I've tried the documentation's value of "kbd-chooser/method=us", values mentioned on Google as 'kbd-chooser/method="American English"' as well as specifying all preseed keyboard selection values I can find in deb conf dumps, but none have worked. I always end up with an interactive "Please press one of the following keys". Once I press the requisite keys, things proceed fine and the rest of the installation works as desired.

Anyone have an exact set of append params from a working, completely automated PXE installation of an Edgy server they could share?

Alternatively, where should I look in the busybox shell to see why this isn't working? I've poked around a bit but haven't found anything useful atm.

-erik

---

### Post by paljas on 2007-03-23
I had the same prob. You have to use:

append vga=normal initrd=ubuntu-installer/i386/initrd.gz ramdisk_size=16417 root=/dev/ram rw  debian-installer/locale=en_US console-setup/layoutcode=us
netcfg/get_hostname=unassigned-hostname

Seems to change sometimes in variuous ubuntu/debian versions...

---

### Post by beeman on 2007-03-25
Thanks paljas, your solution works great... :)

---

