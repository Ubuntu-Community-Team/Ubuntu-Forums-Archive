---
title: "1st a blue screen, then &quot;No Partitionable Media&quot;"
date: 2005-08-09
forum: Installation &amp; Upgrades
---

### Post by Leigh Blackall on 2005-08-09
The first time round installing from the Ubuntu 5.04 for Intell x86 Install CD over a Fedora Core 3 OS, I agreed to have the Ubuntu installer delete the contents of the drive and install over the top of what was there... it hung on a blue screen for about 5 minutes, so I pressed the manual restart button on the front of the box (bad move?). Got through the restart, manually pointing to the primary boot drive (DVD drive) again, but this time, when checking the hard drive during the install it came up with:

[!!] Partion disks
No partitionable media
No partitionable media were found.
Please check that a hard disk is attached to this machine.
<Go Back> <Continue>

I'm stuck! Did my hard drive just die, or did I wipe something I shouldn't have in the first install attempt.

Even though I had Fedora Core 3 on there before, I'm not all that good at using Linux yet.

---

### Post by blind0wl on 2005-08-09
I would suggest booting to your machine with knoppix or win98 boot disk and doing a fdisk /mbr on your drive.

Then when you reboot and run the installer, instead of just hitting enter at the boot sequence, type expert and hit enter.  This will step you through the install.

---

