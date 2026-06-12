---
title: "Kernel Panic - Not syncing.  No Init Found.  UEFI"
date: 2013-07-10
forum: Installation &amp; Upgrades
---

### Post by sarge999 on 2013-07-10
I've been trying to install Ubuntu 13.04 (and a few other flavors of linux) on my Asus cm1745 for about a week now and have gotten nowhere.  I've tried with secure boot, without secure boot, without fast boot, with UEFI, without UEFI and who knows what else.  I usually have the same problem.  Grub loads and gives me a menu, I choose ubuntu and I either am stuck with a purple screen or I get the system to load until it has a kernel panic because no init found.  Any assistance anyone can provide is appreciated. I tried to use the boot repair cd several times to no avail as well.  You can see summaries of some of my attempts here:

[http://paste.ubuntu.com/5862085](http://paste.ubuntu.com/5862085)
[http://paste.ubuntu.com/5858847](http://paste.ubuntu.com/5858847)

As well as my error screen nemesis(attached)



Thanks in advance for any help.

---

### Post by oldfred on 2013-07-10
I do not know about kernel panics. That often is a bad download. Did you run md5sum?
 [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Your system looks ok in CSM/BIOS mode. But some BIOS or grub/Ubuntu have issues with very large / (root) partitions. You might try a smaller 25GB / and the rest as /home and/or NTFS data partition for shared data. Some also have to have a separate /boot inside the first 100GB, but that is more common with USB external installs.

I have seen several others where Boot-Repair has the FIBMAP: Invalid argument error, but do not know what it is. 
Quick Google search says it is an old error related to preload?

---

### Post by sarge999 on 2013-07-10
Thanks, Oldfred.

I haven't md5'd the iso yet, but I have used the same iso to successfully install on other machines.  Moreover, it is not only Ubuntu that won't install.  I was out of luck with Mint and Fedora as well.  The odd thing is that all of them boot just fine from a live-cd.

Since posting this message, I slapped in an additional 320 gb hard drive and installed grub and ubuntu there.  Initially only windows loaded so I used the boot repair cd to fix grub.

Now I am back to the same kernel panic as before.  The summary for the endeavor is listed here.

[http://paste.ubuntu.com/5862895/](http://paste.ubuntu.com/5862895/)

---

### Post by oldfred on 2013-07-10
Again some BIOS do no like large / (root) partitions. Make a 25GB / partition and use rest of 320GB drive as /home. You can test if that is the issue quickly just by shrinking your current / to less than 100GB and see if it then boots (that has worked for about 50% of those I suggest it to).

---

### Post by sarge999 on 2013-07-10
I'll give that a shot and report back to see how it comes out.

---

### Post by sarge999 on 2013-07-10
I shrinked the boot partition down to 24 gigs.  No change....Same error.

---

### Post by oldfred on 2013-07-10
The only other thing I found was to add this boot option. Are you booting with UEFI or BIOS?

BIOS uses the accessibility screen which is shown first. UEFI uses grub which is also shown later as it also is how the screen looks after the install and on first boot, then boot parameters may also be needed.

try this boot option:
init=option

You may also need nomodeset.

        How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)
Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by sarge999 on 2013-07-11
Tried both commands - still no luck.

I also tried installing without UEFI.  Same errors with MOBO in legacy mode. 

I booted the live cd again and noticed that the init file shortcuts are saying that the target where they are pointing doesn't exist.  Don't know exactly what that means but I did confirm there was no init file in /boot.

---

### Post by oldfred on 2013-07-11
Depending on how you are booting, you use syslinux(BIOS) or grub(UEFI) to boot. Syslinux shows accessibility screens and grub has more of a standard grub menu.
In my ISO for 13.04 64 bit initrd.lz is in /casper/.

---

