---
title: "Help!  SATA install?"
date: 2006-03-21
forum: Installation &amp; Upgrades
---

### Post by rainbowjoshua on 2006-03-21
Okay, I'm going to briefly tell the whole story.

My Breezy installation had been running good for a while, but then I got an irresistable urge to upgrade to dapper.  This went poorly.  I'm not going to go into the details of it here, but in the interests of getting my system back up, I got a new hard drive to install a fresh Breezy onto so I could mess with Dapper at my liesure on my old hard drive.

My problem now is that I put my new hard drive in, booted to my trusty breezy install disc, went through the easy installation and came to disk partitioning.  My new 320gb SATA hard drive was detected  (SCSI5) as 250gb, which I don't understand, but I selected it, told the install to format that new hard drive and use guided partitioning.  The formatting of the drive seemed to get stuck at 33% and I was worried, but after being stuck a while, it finally said it was done and started installing packages.  I rebooted like normal, the grub install detected my broken Dapper installation on my other (60gb) hard drive, and everything seemed to go well.

When I tried to boot to my new installation, however, I get

/dev/sda not found!

Now, however, grub has stopped working, and I've removed my old 60gb hard drive because it has my precous data on it, and I'm going to try to reinstall again.  I'm really worried though, so any advice anyone can give on installing on SATA drives is appreciated.

Thanks!
Joshua

---

### Post by rainbowjoshua on 2006-03-21
Okay, well, my installation finished, nothing but a SATA drive, same shit with 33% and the installation finishes normally and I get:

```
GRUB Loading stage1.5.


GRUB loading, please wait...
Error 18
```
And that's all.  Please, I am dismayed.  Is there simply inadequate support for SATA drives?

Thank you.
Joshua

---

