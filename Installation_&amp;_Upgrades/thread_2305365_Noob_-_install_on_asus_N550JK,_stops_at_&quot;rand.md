---
title: "Noob - install on asus N550JK, stops at &quot;random: nonblocking pool..&quot;"
date: 2015-12-05
forum: Installation &amp; Upgrades
---

### Post by nick208 on 2015-12-05
I created an usb stick with Rufus & ubuntu 15.10 and booted from that. First choose Try Ubuntu without installing and it worked fine. Then I rebooted and choose install Ubuntu and it stopped at "random: nonblocking pool is initialized".
Tried searching and found something to do with screenresolution, not sure if its related but figure since I have 3840 x 2160 maybe that has something to do with it?
No idea where to go from here..?

---

### Post by nick208 on 2015-12-07
Any advice?

---

### Post by nick208 on 2015-12-26
Guess thie asus n550jk has problems with ubuntu?

---

### Post by ubfan1 on 2015-12-26
Did you try the Nvidia boot options, like nomodeset?  That is probably the issue, nothing to do with the random pool setup.  See:
[http://ubuntuforums.org/showthread.php?t=2303318](http://ubuntuforums.org/showthread.php?t=2303318)
Other things to try if nomodeset doesn't work:
For UEFI machines (with a black screen grub (grub-efi)  without any
function key options, like the older grub-pc, edit the grub menu and add
the below options on the "linux" line, then boot with F10 or ctrl-X.


Options for Video problems:

nomodeset
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic

Older Intel video card:
i915.modeset=1 or i915.modeset=0
newer:
i915.i915_enable_rc6=1

video=1280x1024-24@60
video=VGA-1:1280x1024-24@60

To allow Nvidia hybrid machines to boot.
nouveau.blacklist=1

Skylake needs this (15.04...):
i915.preliminary_hw_support=1
Maybe
intel_idle.max_cstate=1 nouveau.modeset=0

To slow SSDs to allow them to boot:
libata.force=noncq

---

### Post by nick208 on 2016-01-03
Thank you. I added nomodeset and had it working for a while but then ran into some problems. New to all this so cant explain it too well.
Now I try to create a new live-usb but cant get it to boot. Is the nomodeset supposed to be at the end of the line, after the --? or after "quiet splash", before the "--"?

---

