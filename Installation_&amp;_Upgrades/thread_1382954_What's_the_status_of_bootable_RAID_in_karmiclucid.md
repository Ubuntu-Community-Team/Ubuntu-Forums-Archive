---
title: "What's the status of bootable RAID in karmic/lucid?"
date: 2010-01-16
forum: Installation &amp; Upgrades
---

### Post by leptogenesis on 2010-01-16
I've been trying to figure out what's the best approach to having reliable storage on my ubuntu server.  I'm thinking of using RAID 5, and my main goal is to make my RAID 5 array as easy as possible to maintain.  This means that if *any* of my drives fails, I want to be able to replace it and have ubuntu do the rest.  This is especially important because I most likely won't be the one maintaining the server.

It seems like recent versions of Ubuntu are trying to support bootable software RAID better.  The main problem before was the /boot partition, which needs to get executed before the RAID driver is fully loaded.  The howto on software raid explains the hack that lets this work:

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

It essentially involves tricking GRUB into thinking that your RAID 1 disk isn't actually RAID.  I'm afraid, however, that this would need to be re-done every time a disk fails, and might not survive GRUB updates (as grub can't configure itself through a RAID abstraction layer).  It also seems like a really bad idea to screw around with the raw data that's part of a RAID array.  You might also notice that that how-to is out of date (karmic uses grub2).

More recently, Grub has supposedly started to understand the standard RAID 1 setup (that is, have /boot on a RAID1 partition and have the rest of your data on RAID 5):

[http://grub.enbug.org/LVMandRAID](http://grub.enbug.org/LVMandRAID)

And there's anecdotal evidence that karmic tried to support this, but it doesn't quite work yet:

[http://www.ubuntu.com/testing/karmic/beta#Known%20issues](http://www.ubuntu.com/testing/karmic/beta#Known%20issues)

(see the second bullet point).  It looks like Lucid is hoping to support it fully.

So my question is, what's the process for getting bootable RAID in karmic/lucid?  Will it be possible to set this up straight from the installer in lucid, without any separate Grub setup?

Is there any more information about dos and don'ts for partitioning your disks?  i.e., I know that /boot needs to end up on a RAID1 partition...are there any other restrictions?

What's the actual process for replacing a failed disk assuming you've set the RAID up correctly?  Does Grub automatically configure the new disk to be bootable, or does that need to be done manually?  

Is this process actually endorsed by Ubuntu?  That is, will future updates to Grub/partitioners be able to cope with systems that are set up to boot from RAID?

---

### Post by leptogenesis on 2010-02-05
bump

---

### Post by silentb on 2010-02-06
Hello!

I have installed Lucid on a RAID 0 array and it works. GRUB 2 is able to read files in /boot (yay!) and correctly loads kernel + initramfs.

---

### Post by silentb on 2010-02-06
> Does Grub automatically configure the new disk to be bootable, or does that need to be done manually?

I think you have to install GRUB by hand. Though this is hardly an annoyance.

---

