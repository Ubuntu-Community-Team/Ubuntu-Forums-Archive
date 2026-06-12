---
title: "Aspire one happy not booting"
date: 2011-01-09
forum: Installation &amp; Upgrades
---

### Post by merlin371 on 2011-01-09
So my mom just got an Aspire one happy, and I tough i would put ubuntu netbook edition on it, so I downloaded the ISO and made a bootable usb stick of it, but everytime i boot the netbook i see the SYSLINUX line and then it goes no further, any ideas on what i could do?

---

### Post by kansasnoob on 2011-01-09
> **merlin371 said:**
> So my mom just got an Aspire one happy, and I tough i would put ubuntu netbook edition on it, so I downloaded the ISO and made a bootable usb stick of it, but everytime i boot the netbook i see the SYSLINUX line and then it goes no further, any ideas on what i could do?

Did you check the md5sum of the iso?

Also, is that running Android? I'm not familiar with it so I'm curious what program you used to create the Live USB?

---

### Post by merlin371 on 2011-01-09
> **kansasnoob said:**
> Did you check the md5sum of the iso?

Also, is that running Android? I'm not familiar with it so I'm curious what program you used to create the Live USB?

Didnt do the check no,  and ya is running android incredibly useless tho :P I used both the program that was suggested on the tutorial on the ubuntu page "universal usb installer" and also the app that comes inside the ISO made no difference.

---

### Post by kansasnoob on 2011-01-10
> **merlin371 said:**
> Didnt do the check no,  and ya is running android incredibly useless tho :P I used both the program that was suggested on the tutorial on the ubuntu page "universal usb installer" and also the app that comes inside the ISO made no difference.

Sorry to be dense but are you then saying that you created the live USB using a different machine that's running Ubuntu? Or some other OS?

I've never used "Universal USB Installer".

Here's a bit about md5sum:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Or you might check out unetbootin:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by varnav on 2011-09-19
I have Aspire One 722.

Loaded Ubuntu 11.04 to a USB stick using Unebootin. Booting stucks at message "SYSLINUX 4.03 ....."

Same thing if I try Gparted distro from Tuxboot.

Looks like syslinux is not compatible with BIOSes of latest acer netbooks.

---

### Post by varnav on 2011-09-20
UPD:

Tried another USB flash drive, 2 GB instead of 8 GB and it worked!

---

