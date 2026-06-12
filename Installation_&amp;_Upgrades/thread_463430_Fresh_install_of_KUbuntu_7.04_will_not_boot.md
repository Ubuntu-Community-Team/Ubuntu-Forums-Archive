---
title: "Fresh install of KUbuntu 7.04 will not boot"
date: 2007-06-03
forum: Installation &amp; Upgrades
---

### Post by garyc on 2007-06-03
I figured I would try out Ubuntu, so I downloaded the KUbuntu 7.04 dvd.  The install went ok, but grub did not identify my drives correctly.  Here is my setup (3 SATA drives):

SATA 0 and SATA 1: Software RAID with Windows XP installed.
SATA 2: Single non-RAID drive with Ubuntu (eventually) installed.

Grub configured everything assuming /dev/sdc = (hd2).  That's wrong, because the bios is treating the first two drives as a single RAID drive (hd0).  So the Linux drive is actually (hd1).  I updated menu.lst by adding the command "device (hd1) /dev/sdc" and replaced all occurances of "hd2" with "hd1".  I also updated device.map.  Then I reinstalled grub using these commands:

grub
> device (hd1) /dev/sdc
> root (hd1,0)
> setup (hd0)

That got me a little bit further.  At least now I get to the grub boot menu and it looks like the kernel actually starts to boot up.  But then it freezes with very little explanation.  Here are the last messages I see when booting in single user mode:

Begin: Running /scripts/init-bottom ...
Done.
init: Error parsing configuration: No such file or directory
[7.139663] Kernel panic - not syncing: Attempted to kill init!

I have no idea what file init is looking for... Anybody have any ideas?


Update:
I took a leap and guessed that this whole problem was related to my RAID setup.  So I eliminated the software RAID and now I only have two SATA drives (non-RAID).  Windows is obviously on drive 0 (/dev/sda) because it has to be.  My goal is now to install KUbuntu on drive 1 (/dev/sdb).  I pretty much flew through the install with no problems whatsoever.  I saw no warning or errors of any kind.  Ubuntu copied all of the files, set up grub, installed the MBR and all with no intervention on my part.  So I take out the DVD and reboot... same exact error.

I'm not looking for someone to solve this problem outright, but surely there must be more that I can do to dig down into the actual cause of this error.  Is there any type of logging or debugging I can enable?  "No such file or directory" is way too general to even begin troubleshooting.  Surely, there must be some way to troubleshoot startup problems other than just looking at the console and hoping it tells you something useful (which it isn't in this case).  Any helpful tips of any kind would be greatly appreciated.

Another Update:
The issue is resolved.  The KUbuntu bootup procedure only mounts the root partition and then apparently tries to get files from the other partitions before they're mounted.  Rather than go through any more troubleshooting, i just created a single root partition with everything on it.  That worked.

---

