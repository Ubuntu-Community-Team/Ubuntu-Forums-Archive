---
title: "Kernel panic- not syncing: VFS: Unable to mount root fs on unknown-block (0,0)"
date: 2010-11-10
forum: Installation &amp; Upgrades
---

### Post by Rodart on 2010-11-10
Hello,I'm trying to install ubuntu 10.10 on this old pc that I don't use since 1998, I boot up the cd Install it, and when it reboots and loads ubuntu I get this error message: "0.560882 Kernel panic- not syncing: VFS: Unable to mount root fs on unknown-block (0,0)
Pid: 1, comm: swapper not tainted 2.6.35-22-generic #33-ubuntu
call trace:
c05c6468 ? printk+0x2d/0x35
and other things like that one, it's a lot to copy here, how can I solve this?
Thanks!

---

### Post by dino99 on 2010-11-10
often seen recently, check your bios to set it on: AHCI or better on COMPATIBLE if you have the choice (check for bios update too)

---

### Post by Rodart on 2010-11-10
I searched for that option in the BIOS but I can't find it, the motherboard is a m805lr from the year 2000. Also I have no idea how to flash or update the BIOS.
thanks

-Update PCchips says that the motherboard is discontinued and nobody on earth has any other bios updates for it. Any solutions or ideas will be appreciated.

---

### Post by ezsit on 2010-11-10
Use newer hardware or older operating system, eventually you will find a balance.

---

### Post by Rodart on 2010-11-10
> **ezsit said:**
> Use newer hardware or older operating system, eventually you will find a balance.

So, it should work with an older Ubuntu?

Update: I will try with gutsy ribbon

---

### Post by Rodart on 2010-11-11
I tried with 9.10, but I get a "initrd is too big":( Error, should I start a new thread?
THanks!


And I don't have " memory hole" option on the bios

I tried with gutsy ribbon too, but I can't get past the installation throws some runtime error I didn't save. Maybe an even older version ? anyone has a link?

Or maybe another linux distribution that I could use, I only know how to use ubuntu right now.
Update Gutsy ribbon gets stuck at 90% I will try 7.10 alternate

---

### Post by Rodart on 2010-11-14
Gutsy is working fine but I can get the updates because the content is not online anymore is there any way to get the updates ??

---

### Post by blaumeer on 2010-11-17
I have the same issue with new hardware and 10.10 maverick. My laptop has an InsydeH20 BIOS version Q3G62, the hard disk controller is configured as AHCI.

Once in every two boots it fails with:

kernel panic not syncing vfs unable to mount root fs on unknown-block(0,0);
swapper not tainted 2.6.35-23-generic etcetera

Evary second boot is successful, provided I select the kernel from the grub2 menu.

What I have tried so far:
- upgrade the system to maverick-proposed;
- switched to a 2.6.36 kernel;
- regenerated initramfs images:;
- update-grub;
- installed startup manager, an ubuntu gui for configuring grub2;

It's really odd. My system has an LVM + encrypted disk setup (did a fresh alternate-install), proprietary nVidia GPU drivers are enabled.

---

### Post by crazyarlo on 2010-11-18
I have exactly the same problem, on an IBM Thinkcentre 3 ghz Pentium 4 desktop with a SATA hard drive.  I installed Grub 2, to no avail.  I need a working Linux box!!!  This is very discouraging... I have never had an issue with Ubuntu on any machine!!!

I may have to go with Debian, or Fedora.  I love the interface tweaks that Ubuntu has made, but I can't live with this crap.

Newer computer or older version?  Isn't that what Microsoft says???

---

### Post by dino99 on 2010-11-18
on my system i always have a boot failure the first time, so i make an other cold boot and it usually work. The Linux kernel(s) have numerous acpi issues, so i suggest:

- use one of the latest kernel: 2.6.37 work fine most of the time
- to get around boot failure, try to boot by adding either: noacpi, nolapic, noapic, nomodeset, irqpoll (edit the boot line of grub menu and add this parameter at the beginning of line where you see "quiet splash" (these last ones can be removed if you want to know on screen what happen when booting)

---

### Post by blaumeer on 2010-11-19
Thank you dino99, very interesting cues since it really is a boot issue.
I tried kernel 2.6.36 which has the same issue. Now let's try 2.6.37 which has a very recent rc2 dated Nov 16. EDIT: so far 2.6.37 has solved the problem.

Another direction I am considering investigating is nVidia driver nvidia-current 260.19.06 or virtualbox-ose.

---

### Post by blaumeer on 2010-11-25
The new kernel did not resolve the issue.

---

### Post by ge0ffrey on 2010-12-14
I am having the same exact problem as blaumer on a brand new HP Z400.
Is there a bug in launchpad for this already?

---

### Post by ge0ffrey on 2010-12-14
Might be related: [https://answers.launchpad.net/ubuntu/+question/137642]("https://answers.launchpad.net/ubuntu/+question/137642")

---

