---
title: "No menu after Karmic installed into Windows 7"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by joemilx on 2009-11-25
I have a fresh Windows 7 install and installed 9.10 into the Windows 7, but on a separate drive.  Everything seemed to work during the install.  On reboot, I went straight into Win 7 without ever seeing a GRUB menu.  Any ideas on how to proceed?  Thanks in advance.

---

### Post by overdrank on 2009-11-25
> **joemilx said:**
> I have a fresh Windows 7 install and installed 9.10 into the Windows 7, but on a separate drive.  Everything seemed to work during the install.  On reboot, I went straight into Win 7 without ever seeing a GRUB menu.  Any ideas on how to proceed?  Thanks in advance.

Hi and if you installed Ubuntu on a separate drive then the grub was install there.  You may need to  reinstall the grub of you may also be able to select to boot to that drive in bios.

---

### Post by Mark Phelps on 2009-11-25
> **joemilx said:**
> I have a fresh Windows 7 install and installed 9.10 into the Windows 7, but on a separate drive.  Everything seemed to work during the install.  On reboot, I went straight into Win 7 without ever seeing a GRUB menu.  Any ideas on how to proceed?  Thanks in advance.

What is most likely the problem is that your install of Win7, since it was the RC, used the new default two-partition setup -- with one boot partition and one OS partition.

We have LOTS of posts here (with no one posting any solutions) about just that situation -- Win7, 2-partitions, Wubi, Ubuntu 9.10.

What it appears is that the combination of the 2-partition Win7 setup, Wubi, and GRUB2 (in Ubuntu 9.10) simply does NOT work.

If anyone reading this KNOWS different (as in exactly HOW to fix this), would love to hear back.

---

### Post by joemilx on 2009-11-25
This was the retail Win 7 (32 bit), not the RC.  I see only one Win 7 partition.

---

### Post by joemilx on 2009-11-27
Downloaded fresh copy of Karmic 32-bit and installed within Win 7.  Now I get a Windows Boot Manager menu with Win 7 and Ubuntu options.  If I select Ubuntu, I go to the familiar GRUB menu which lists both the 32-bit inside-Win 7 install and the 64-bit Karmic install I did several days ago on a separate drive.  It also lists an entry for each of the four partitions on the primary drive even though only the first partition contains a Windows install.  The last three entries are listed as Win XP.  Looks like os-probe is being over-zealous.

I'll keep playing to get down to a single (GRUB) menu.  Interestingly, when I did a 64-bit Win 7 Pro and 64 bit Karmic install on another PC, I got a good GRUB-only menu right after the Karmic install.  Not sure where the Windows Boot Manager menu came from on these installs.

---

### Post by darkod on 2009-11-27
> **joemilx said:**
> This was the retail Win 7 (32 bit), not the RC.  I see only one Win 7 partition.

In case this is confusing you, in Computer you would see just the one partition, C:. The small 100MB is called System Reserved or something and can be seen in Disk Management for example. Control Panel, Administrative Tools, Computer Management, Disk Management.
Or just windows button +R and type diskmgmt.msc

Only a disk management tool that shows you all partitions will show you this 100MB system recerved one.

---

