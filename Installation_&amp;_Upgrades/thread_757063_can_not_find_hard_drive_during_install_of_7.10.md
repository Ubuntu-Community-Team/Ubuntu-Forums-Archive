---
title: "can not find hard drive during install of 7.10"
date: 2008-04-16
forum: Installation &amp; Upgrades
---

### Post by locksmith54 on 2008-04-16
I am a newbie at Linux. I am try to install Ubuntu Desktop 7.10 on a Dell Optiplex GX280. Intel Celeron 2.53 GHz with 512 M.  The disk is 74.5 G with a partion of 37.25 G NTFS with Windows XP Pro Service pack 2 installed. The remaining 37.25 G is free space.  

The XP system boots and runs. The Live CD runs fine. When I do the install I get to the prepare partions screen and it shows no devices. I have ran the "Check CD for defects" on the splash screen and it shows no problems. 

I also downloaded Kubuntu Desktop 7.10 and am experiencing the same problem.

---

### Post by Shazaam on 2008-04-16
Try this....
Boot the Ubuntu livecd again and run the partition editor by itself (System>Administration) to see if it shows the partitions/free space. If not you may need to run a separate partitioning program and pre-setup partitions. The gparted livecd is the one I use. Once you have them set up you would point the Ubuntu installer to those pre-made partitions.

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

The way I had mine set up is this.....
1. Windows first.
2. Added Extended partition filling free space.
3. Added a /swap partition (logical) inside Extended partition 
4. Added Ubuntu (logical partition) inside extended partition.

---

### Post by prshah on 2008-04-16
> **locksmith54 said:**
> 
The XP system boots and runs. The Live CD runs fine. When I do the install I get to the prepare partions screen and it shows no devices. I have ran the "Check CD for defects" on the splash screen and it shows no problems. 


Change your SATA options in the BIOS to "Legacy", from "Native". It may also be called "IDE Compat" or something else; just switch it about, boot from the live CD, install ubuntu, then go back to the BIOS options and put it back as it was. You have to do this ONLY during installation; subsequently everything will be gangbusters.

WARNING: Do not boot into XP without changing the settings back!

---

### Post by locksmith54 on 2008-04-16
Shazaam,
When I run gparted from the live cd, it comes back with a message saying "no devices detected".

Prshah,
I changed the SATA Operation from Normal to Combination (the only options shown) in the BIO's.  There was still no devices found.

---

### Post by prshah on 2008-04-17
> **locksmith54 said:**
> 
Prshah,
I changed the SATA Operation from Normal to Combination (the only options shown) in the BIO's.  There was still no devices found.

There will be some other options related to SATA. If you can post a screenshot (digital camera?) of the first bios screen I can probably suggest something.

This problem of SATA drive not being found during installation of Ubuntu and/or XP (Yes, during INSTALLATION of XP, the same problem occurs, since SATA device drivers are not loaded.) is a recurring problem; maybe some other posts on this forum can suggest a more suitable BIOS option.

---

