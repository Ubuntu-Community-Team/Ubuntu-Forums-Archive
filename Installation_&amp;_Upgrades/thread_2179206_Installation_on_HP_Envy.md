---
title: "Installation on HP Envy"
date: 2013-10-07
forum: Installation &amp; Upgrades
---

### Post by derek-archer on 2013-10-07
Hi all, I just purchased a HP Envy 4 Sleekbook, mainly because it's on the list of supported hardware. 
I originally bought a Sony Vaio but had no end trouble with Ubuntu on it and returned it to the retailer and took home the HP. For this reason I don't want to wipe windows from the hard drive yet. If I can't install Ubuntu I want the option of taking it back to the retailer. At the very least, I want to keep the recovery partitions for windows in case it all goes legs up.

I want to install 12.04.3 LTS 64 bit, but I've run into one main showstopper.
So, I can boot from my USB drive and choose "try Ubuntu". It boots into the live session no worries and all of my hardware appears to work. I choose install, and get as far as the "Installation type" window and there are no partitions available to install to.
So far I've tried installing with secure boot disabled; legacy boot enabled; created a new partition in windows to install to; and tried the "install ubuntu" option rather than boot into a live session.
So, questions.
1. Why isn't the install process able to see the hard drive?
2. Has anyone else had this issue?

Any help will be greatly apreciated.
Cheers, Space Chimp.

---

### Post by mastablasta on 2013-10-07
> **derek-archer said:**
> So far I've tried installing with secure boot disabled; legacy boot enabled; created a new partition in windows to install to; and tried the "install ubuntu" option rather than boot into a live session.
So, questions.
1. Why isn't the install process able to see the hard drive?
.


you have 4 primary partitions on your drive. so it's already maxed out. You need to change one into secondary/logical. mini partition tool will help you change one into logical (for example the system partition). good luck!

also don't "create new partition" in windows, create empty (unformatted) disk space instead.

---

### Post by derek-archer on 2013-10-07
Thanks for the very helpful info Masterblaster. Sure enough, there are four OEM partitions sitting there.
Cheers,
Space Chimp.

---

### Post by fantab on 2013-10-07
Since it is a latest purchase, Does it boot with UEFI? If it does then your HDD will have GUID partition table [GPT] which supports more than 4 Primary Partitions. Also to install in UEFI you will need to boot Ubuntu DVD/USB in UEFI mode and install it as such.

The output of the following from Live Ubuntu will tell us if your HDD has GPT or MSDOS partition table...
```
sudo parted -l
```

Why don't you clone your HDD with any Windows Cloning software and keep is aside, just in case you need to re-run to the retailer....

---

