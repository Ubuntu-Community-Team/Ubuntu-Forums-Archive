---
title: "Laptop install hangs"
date: 2008-03-26
forum: Installation &amp; Upgrades
---

### Post by MarcosDurrant on 2008-03-26
A month or so ago my laptop (a Dell inspiron 1100) froze up and after rebooting it wouldn't load Ubuntu 7.10.  So I proceeded to just reinstall but I have been having issues ever since.  The majority of the times that I attempt to install I get either a "logical block" error or it just hangs on the install when it gets to partitioning the hard drive (I have let the computer just sit overnight to see if it was just being super slow on the partitioning but to no avail).  A few weeks ago I was able to successfully install Debian and then I was also able to install 5.10 but then I tried to upgrade and now it won't install either.  I have tried every distro that I can imagine - Suse, 5.10, 6.04, 7.10, 7.04, 8.04, Linux Mint, Fluxbuntu, Freespire, etc.  Any suggestions on what to try?  Initially I thought it was a hard drive failure but when I was able to install Debian and 5.10 it made me think it was something else...  And I have tried to install of off distros that I have burned myself and off of the official Ubuntu CDs.  Any help is appreciated!

---

### Post by DellCA on 2008-03-28
> **MarcosDurrant said:**
> A month or so ago my laptop (a Dell inspiron 1100) froze up and after rebooting it wouldn't load Ubuntu 7.10.  So I proceeded to just reinstall but I have been having issues ever since.  The majority of the times that I attempt to install I get either a "logical block" error or it just hangs on the install when it gets to partitioning the hard drive (I have let the computer just sit overnight to see if it was just being super slow on the partitioning but to no avail).  A few weeks ago I was able to successfully install Debian and then I was also able to install 5.10 but then I tried to upgrade and now it won't install either.  I have tried every distro that I can imagine - Suse, 5.10, 6.04, 7.10, 7.04, 8.04, Linux Mint, Fluxbuntu, Freespire, etc.  Any suggestions on what to try?  Initially I thought it was a hard drive failure but when I was able to install Debian and 5.10 it made me think it was something else...  And I have tried to install of off distros that I have burned myself and off of the official Ubuntu CDs.  Any help is appreciated!

Usually, a "logical block" error is a failure with the hard drive.  The fact it hangs while partitioning the drive would help confirm that is the problem.  I'd recommend getting a replacement hard drive for the system.  The Inspiron 1100 uses a standard mini-IDE drive.  The documentation shows they shipped with up to 40Gb hard drives of either 4200 or 5400 RPM (the faster the drive RPM the more battery power it takes to run the drive, but the faster the response time as well).  

I don't remember if it is the 11mm or 13mm height drive, so I would recommend bringing the hard drive you have now with you when you go to get the replacement.  The reason the height matters is that the carrier (plastics) for the drive will only support a specific height of hard drive or smaller, and from memory I believe it uses the 11mm drives.

The only other thing to watch out for with a replacement drive is that I believe the motherboard only supports drives of 128Gb or less.  I am not 100% sure on this, and it is possible that a BIOS update removes that limitation, but it is something you will want to keep in mind when getting a replacement drive.  If you have a 160Gb or larger drive you can test on the system before buying one that will tell you for sure.  Even if you buy a larger drive but the board only reads 128Gb, you can still use those 128Gb as the rest are just not listed.

The instructions for removing the hard drive from the carrier are available in the [service manual](http://support.dell.com/support/edocs/systems/ins5100/en/sm/hdd.htm#1084976) for the system.  That manual is available from the Dell support website ([http://support.dell.com](http://support.dell.com)). Unfortunately, it does not list how to remove the drive from the carrier.  That, however, just involves removing the screws on the side of the drive carrier assembly and pulling the drive out.

When you switch drives make sure to move the interposer board (an adapter that goes onto the IDE connection on the drive to convert from 40-pin IDE to a slot connection on the motherboard) from the old drive to the new one.

If you have any questions on this I'll be happy to answer them.

Larry
Dell Customer Advocate

---

