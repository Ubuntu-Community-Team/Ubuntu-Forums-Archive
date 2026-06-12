---
title: "Ubuntu (any version) on PS3 w/Kboot?"
date: 2014-10-04
forum: Installation &amp; Upgrades
---

### Post by James_Spinella on 2014-10-04
Hey all,

I'm no stranger to Ubuntu nor the forum, but I am a new user.

I have an original PS3 with very old (3.15) firmware, and it still has official OtherOS support. I used a flash drive to install Kboot, and the hard drive is formatted as per the instructions on Sony's website. I can boot into Kboot, with the signature pair of Tux penguins, where it complains that "[COLOR=#333333][FONT=monospace]No defualt root fs was found, or one was found and it didn't containg a message = congig file."[/FONT][/COLOR]

It's kind of detailed here [https://bugs.launchpad.net/ubuntu-ps3-port/+bug/376674](https://bugs.launchpad.net/ubuntu-ps3-port/+bug/376674) but that's *after *installing Ubuntu, and has to do with Ubuntu formatting / as ext4 instead of ext3, which is necessary because the PS3 cannot read ext4.
 
My problem is that Kboot isn't picking up the Ubuntu 12.04 PPC CD that I used to install Ubuntu on the very same PS3 with Petitboot on later CFW (which ended up being too slow to use) or the USB drive with Ubuntu 10.10 PPC+PS3 that Petitboot would also recognize and boot from. For clarification, I went to 3.15/official OtherOS/Kboot because Ubuntu was so slow with the CFW "hack" method and I could not get the HDD to partition properly (so I had to reformat HDD to boot GameOS).

There are threads with this issue all over the Internet, and I've been unable to find a solution. Any ideas?

---

### Post by James_Spinella on 2014-10-10
I figured it out...

I have Rebug 3.55 OtherOS++ CFW installed, but the GameOS firmware shouldn't matter so long as you have Petitboot installed.

In the case of Rebug, you must install Rebug Toolbox, use it to install Petitboot (it'll tell you which file to get from the Internet, just put it on the root of a FAT -formatted flash drive) on the NAND flash of the PS3, and then use it to boot OtherOS (apply ALL Lv1 patches when it asks!).

1. Use Petitboot (0.2, the non-GUI version, is what I have) and burn a CD/DVD (flash drives won't work) of Ubuntu for PPC.
2. Boot from CD and install Ubuntu to PS3 HDD (for the life of me, I cannot get the HDD to partition for OtherOS, so I have to use the entire 60GB HDD, leaving me without GameOS unless I reformat the HDD, which of course deletes Ubuntu).

**Things to note:**
- It takes a really long time to install Ubuntu (something like 3-4 hours)
- The PS3 has 256MB of RAM, I suggest using an Ubuntu Server iso so that you don't eat through the RAM with the GUI.
- I get an error when trying to install Ubuntu 14.04 Server (PPC version of course), so maybe try 12.04 Server (I don't have any more blank CDs to try it with).
- At least with me, flash drives will always be detected, but CDs will only be detected (by Petitboot at least) on the FIRST BOOT of Petitboot/OtherOS after leaving GameOS.
- So if you reboot the PS3 and put a CD in, it WILL NOT WORK. You will have to boot back into GameOS and then either format the hard drive again and then use GameOS to boot into OtherOS/Petitboot or just use GameOS to boot into OtherOS/Petitboot. You may or may not have to reformat in order to get Petitboot to see the CD.

[B]Other Thoughts
[/B]- It may be possible to use the GUI if you replace your PS3's hard drive with an SSD (worth a shot if you have one laying around), since it's really not all that slower than RAM when used as SWAP.

---

