---
title: "Unable to Install GRUB"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by themaven on 2007-04-24
Hi,

I was installing Fiesty on my VAIO laptop. I have a 60GB hard disk with 2 partitions - the first one is about 15 GB and has Windows XP (and another 5 GB for recovery data). The remaining 40GB I manually configured so that 20 GB was for the Ubuntu installation, 19 GB for data and 1 GB for swap. Device for boot loader installation was set as hd0 by default.

After about 94% of the installation was complete, it started to install the boot loader when it gave me the error:

Unable to install GRUB in (hd0)

Executing grub-install (hd0) failed
This is a FATAL error!

After this the installation exited.

Any pointers on what could have gone wrong and how I can complete the installation?

Thanks!

---

### Post by dcstar on 2007-04-24
> **themaven said:**
> Hi,

I was installing Fiesty on my VAIO laptop. I have a 60GB hard disk with 2 partitions - the first one is about 15 GB and has Windows XP (and another 5 GB for recovery data). The remaining 40GB I manually configured so that 20 GB was for the Ubuntu installation, 19 GB for data and 1 GB for swap. Device for boot loader installation was set as hd0 by default.

After about 94% of the installation was complete, it started to install the boot loader when it gave me the error:

Unable to install GRUB in (hd0)

Executing grub-install (hd0) failed
This is a FATAL error!

After this the installation exited.

Any pointers on what could have gone wrong and how I can complete the installation?

Thanks!

I believe that the Grub loader has to be in the first 1023 logical cylinders of a drive, so possibly the 20GB taken up by the previous partitions doesn't allow this.

You might want to try booting up a Linux Rescue CD with **gparted** on it, and moving the Windows partitions towards the end of the disk so you can have space for the Linux partition at the start. That may make the difference if it is the problem I outlined.

---

### Post by themaven on 2007-04-24
Hi David,

Thanks for the suggestions. But after the installation had failed, I had tried rebooting the system without the live CD and I got an error message "Operating System Not Found"!

As another workaround, I had the 5.10 installation CD (yeah, I know it's really old :-) ) and began the installation in Expert mode and guess what? The GRUB installation worked and at the end, I got the dual-boot menu and can now boot into both Ubuntu 5.10 as well as Windows XP.

For the next couple of days, I now plan to use 5.10 and get familiar with Ubuntu before upgrading to 7.04 :)

Thanks for your help!

Regards,
UV.

---

### Post by themaven on 2007-04-27
Thought I would update in case it helps others :-)

i tried 7.04 installation using the alternate CD and it worked just fine!

now have GRUB loading without issues and dual boot is working properly as well!

---

