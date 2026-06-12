---
title: "No Bootable Device after Natty Install"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by m3s3lf on 2011-04-29
So, I tried upgrading to Natty last night through the update wizard and the install went perfectly... until I rebooted and it got stuck at a screen with an "_" in the top left corner of the screen and nothing else.  I guessed that this was a grub problem, so I tried reinstalling grub2, but to no avail.

So, I burned a Natty install CD and proceeded to reinstall, formatting the partition (/home was on another partition and did not get formatted).  Again, the install went great, rebooted and this time I get "No Bootable Device - Please insert a bootable device and hit enter".

So, again, I try re-installing grub2 from the live CD.  I purge, uninstall, and reinstall grub2... nothing works!  What the hell?

I'm about to my whits end.  Any help is appreciated!

Thanks,
Billy

---

### Post by m3s3lf on 2011-04-29
Oh yeah, this is 32 bit, one hard drive w/ 3 partitions - two are EXT4 and the last is the SWAP.  I can mount the / partition and CHROOT and all of that mess, but I can't get it to boot to save my life!
Thanks,
Billy

---

