---
title: "Runs and Installs from live CD, After install wont boot"
date: 2010-01-01
forum: Installation &amp; Upgrades
---

### Post by erilidon on 2010-01-01
I have been using ubuntu for about a year now and haven't had any major issues. However I just upgraded to a Quad Core AMD Phenom II X4 945, 3.0GHz Processor on a ASUS M4A785-M Motherboard.

The system will boot and load ubuntu 9.10 from the live CD however after the install it will not boot. I don't even see grub load. It just comes up to a flashing cursor.

Ubuntu is the only operating system currently loaded, I had been trying a copy of Windows 7 and it loaded up and saw everything just fine. However it has now been completely removed. - So I know the hardware works.

I am not sure if this is a grub issue, a bios issue, hardware conflict or something else.

Thanks for your help I hope that I can get this working as I don't want to be stuck using Windows 7.


**EDIT: I got it working**. Apparently grub didn't like my RAID I had setup. I removed the RAID configuration and the two drives that were in the raid and ran the install on the hard drive which I was wanting to install it on.

Then after running updates and insuring that grub2 was installed I reconnected and configured the RAID and the system is up and running.

---

