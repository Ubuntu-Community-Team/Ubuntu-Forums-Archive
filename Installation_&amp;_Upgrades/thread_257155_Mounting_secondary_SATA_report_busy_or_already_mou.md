---
title: "Mounting secondary SATA report busy or already mounted after new kernel installed."
date: 2006-09-14
forum: Installation &amp; Upgrades
---

### Post by perimere on 2006-09-14
Hi guys,

I've had a google and search through the forums so apologies if this has already been answered somewhere!

My internet conenction at home is currently broken (not me BT broke it!), so this has compounded my ability to troubleshoot this issue (or use APT).

I have a new system, clean install of Ubunutu Desktop 6.06 with no hassles during install. 

I have 2 SATA drives:
1 x 37GB WD Raptor, which Ubuntu is installed to (no other OS on system).
1 x 500GB WD disk, which is NTFS v5 (formated in XP Pro) full of data.

The problem:
When I boot off the default kernel in Ubuntu I can access the second disk without any issues.

So I built a nice SATA RAID 5 disk using a Highpoint Rocket RAID card and 3 x 500GB WD disks. The instructions to install on Linux  lean towards patching the kernel.

As I have no net at home currently I downloaded the 2.6.17.13 kernel from [www.kernel.org](www.kernel.org) at work and transferred it to my home PC via USB drive.

I followed the steps in:
[http://www.ubuntuforums.org/showthread.php?t=217657&highlight=compile+2.6.17+kernel](http://www.ubuntuforums.org/showthread.php?t=217657&highlight=compile+2.6.17+kernel)

During: make xconfig I am able to see the option for the new RAID controller. No other options where changed from the default config file copied into the kernel source tree, so I've not changed anything.

The kernel compiles fine, but when I reboot, I am no longer able to mount the 500GB disk.

Under Administration | Discs, the Disc Manager application sees the 500GB disk, but labels it inaccessable. Clicking the enable button on that page does not resolve the issue.

fdisk -l shows that the disk is present, but when I type mount -a, or mount /dev/sdb1 I receive the following error:
"Disk already mounted or /dev/sdb1 is busy".

I have tried this with the 2.6.26.16 kernel as well (also from kernel.org). And have repeated both tests without patching the kernel with the RAID drivers. Just a straight compile with the existing renamed .config file lifted from /boot.

The minute I boot back into the default 2.6.25.16 kernel that Ubuntu installed, I have access back to the 500GB disk?

Has anyone seen this before, or have any constructive suggestions?

Of course when I get net access back at home it should make life easier to sort this out.

Thanks in advance.

perimere

---

### Post by perimere on 2006-09-14
I left out a small piece of relevent information earlier - this is a 64-bit machine running 64-bit Dapper ....

Any suggestions greatly appreciated :-)

---

### Post by sebbe1991 on 2006-09-14
You need the [BD-Claim patch]("http://evms.sourceforge.net/install/kernel.html#bdclaim")

---

### Post by perimere on 2006-09-14
Ahhhh thanks sebbe1991,

Your post nudged me out of my daze.

I re-googled, after reading your link, and settled for a simpler solution (for me anyway).

I removed the evms package:
```
apt-get remove evms
```

Problem solved.

Cheers

perimere :)

---

### Post by jspring on 2006-10-27
Thanks, guys.  You helped me as well.

---

