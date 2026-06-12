---
title: "Booting leaves me at a Grub prompt ?"
date: 2010-04-16
forum: Installation &amp; Upgrades
---

### Post by Julian David Pitt on 2010-04-16
After being offered a distribution upgrade yesterday 15/04?, I am now unable to boot. The upgrade seemed to go ok but left me with an 800x600 resolution. I tried to fix this by installing the nvidia drivers for my card which I was offered, but no joy. The screen flashed following the driver install and left with a boot screen showing Ubuntu 10.04, the only escape from which was a reboot. This resulted in this thread **[http://ubuntuforums.org/showthread.php?t=1384669]("http://ubuntuforums.org/showthread.php?t=1384669")**which has not had any response as yet. I have followed the grub 2 LiveCD install guide has fixed the ```
error: the symbol 'grub_puts' not found
``` and now leaves me at a grub prompt. I have been looking around the web for fixes and see there is a bug logged at **[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/496435/]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/496435/")**. It says a fix has been issued but I am unsure how to apply it. Do I just run an update from a Live CD?

---

### Post by Lightstar on 2010-04-29
I'm getting this weird error right now, after installing Ubuntu 10.04.

It's odd, it throws me to Grub Rescue>

---

### Post by infamous-online on 2010-04-29
The problem I'm getting with Ubuntu 10.04, I'm getting a million I/O errors, and it just sits there. If I reset the machine, it goes to a bash shell and that's it. What's going on here? :mad:](*,)

---

### Post by Lightstar on 2010-04-29
Fixed my problem.
The Bios and Windows would see my SATA II drive as primary, my old IDE as secondary.
Ubuntu and Grub would see my old IDE as primary, SATA as secondary, it's odd.

If you get alot of I/O errors, it doesn't sound too good, i'd run a chkdsk check disk thingy, you can probably do it from the live-cd.

---

### Post by infamous-online on 2010-04-29
> **Lightstar said:**
> Fixed my problem.
The Bios and Windows would see my SATA II drive as primary, my old IDE as secondary.
Ubuntu and Grub would see my old IDE as primary, SATA as secondary, it's odd.

If you get alot of I/O errors, it doesn't sound too good, i'd run a chkdsk check disk thingy, you can probably do it from the live-cd.

The disk was fine, however I just tried another clean install and it worked. Strange!

---

