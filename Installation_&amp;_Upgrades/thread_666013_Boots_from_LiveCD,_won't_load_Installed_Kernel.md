---
title: "Boots from LiveCD, won't load Installed Kernel"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by coolaj86 on 2008-01-12
I have a wonderfully old 233mhz pentium-mmx system that once ran Ubuntu 5.04 just fine. Today I booted up the 6.06 LTS LiveCD (I want to use an app which uses 6.06 in the tutorial and I want to follow it quit exactly) and proceeded to install my system. Everything went fine... until it finished.

After the installation the system restarted as per usual.
Grub loads as per usual.
Grub executes
root
kernel /vmlinuz-blah-blah
initrd /initrd-blah-blah
boot

and then before it gets to the usual Uncompressing Linux the system restarts. I've managed to press the Pause / Break key just a moment before the reboot to check for any possible error code but I see none.

I tried loading the BIOS defaults, but that didn't do any good either.

My best guess is that this is a problem with grub and my system.

Any ideas would be appreciated.

P.S. I've had a similar problem trying to install this version of Ubuntu on VirtualBox but it does actually get to the Uncompressing Linux stage and then hangs.

---

### Post by overdrank on 2008-01-12
HI and have you checked the cd for errors and you may also look here
 to do a checksum on the cd 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

