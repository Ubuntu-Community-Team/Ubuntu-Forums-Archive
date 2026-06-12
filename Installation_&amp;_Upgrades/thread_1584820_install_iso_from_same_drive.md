---
title: "install iso from same drive"
date: 2010-09-29
forum: Installation &amp; Upgrades
---

### Post by GNUoob on 2010-09-29
Is it possible to install ubuntu from the same hdrive that you want to put it on? I am thinking i would have to format it into two drives first then put the iso on one and then install to the other.

I have an old laptop that does not boot from CD or USB
It does boot from floppy or hard drive

I want to pull the hd and format it into two? then put it back in and boot from a tomsrtbt floppy to then tell the 1gig partition (iso on it) to install ubuntu to the other larger 39gig partition (final home).

Will this work?

---

### Post by oldfred on 2010-09-29
If you remove it to repartition why not do the install and then plug it back in?

You can create a 1GB grub2 partition with the ISO and boot that.

Direct boot on hard drive:
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

### Post by GNUoob on 2010-09-29
> **oldfred said:**
> If you remove it to repartition why not do the install and then plug it back in?

I have tried that but "X" is not configured and I am unsure about how to reset it to get it working.


--- 
Now going to look at your other links 
thanks :)

---

### Post by oldfred on 2010-09-29
Do not install any proprietary drivers. then on boot if it has problems use e on the grub menu and add parameters to make it work.

I have nvidia and my monitor went to standby & had to do this:
boot from the cd, press F6 and then select the nomodeset option.
(I acutally edited my grub.cfg as I use grub2 to directly boot ISO on USB, or in USB's syslinux.cfg or text.cfg)
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
    * Older Intel video card: i915.modeset=1 or i915.modeset=0
    * nVidia: nomodeset
    * Generic: xforcevesa
    * Radeon: radeon.modeset=0
Other workarounds:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) 
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

Someone recommended this one:
use the uvesafb to fix all the problems
[http://idyllictux.wordpress.com/](http://idyllictux.wordpress.com/)

---

