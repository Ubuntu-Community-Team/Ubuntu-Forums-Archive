---
title: "Installation errors"
date: 2008-07-03
forum: Installation &amp; Upgrades
---

### Post by Giegue on 2008-07-03
I'm very new to Linux, and am trying to install Ubuntu onto a Dell Optiplex GX280. At a certain point in the installation, I keep getting an error. It gets to Step 4, sets up the partitioner, then gives me four choices. I choose the default:

"Guided - resize SCS!1 (0,0,0), partition #1 (sda) and use freed space"

I click next, and it brings up a smaller window about writing the previous changes to disk. I click continue, and get the following error:

"An error occurred while writing the changes to the storage devices. The resize operation has been aborted"

It then continues to the next screen, which has one partition, then free space. I try to continues, and it say:

"No root file system is defined. Please correct this from the partitioning menu"


Any help would be greatly appreciated.

---

### Post by Pumalite on 2008-07-03
Are you trying to dual boot? XP? Vista? If XP; use Gparted Live CD and shrink the XP partition. If Vista; use the Vista partitioner.
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://ubuntuforums.org/showthread.php?t=464425](http://ubuntuforums.org/showthread.php?t=464425)

---

### Post by Giegue on 2008-07-03
There is no other OS on the system. As far as I know, the only thing on this computer is Ubuntu.

Actually, I think there are remnants of a Windows XP OS that didn't install correctly.

---

### Post by Pumalite on 2008-07-03
Then use Gparted Live CD to delete anything left in the drive and format it ext3. Then install Ubuntu>Guided>Use Entire Disk.
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.

---

### Post by Giegue on 2008-07-03
I booted that disk, and when it got to a window, all the text was incredibly small. Way too small to read, so I had no idea what to click.

---

### Post by Pumalite on 2008-07-03
Try Partition Editor from the Ubuntu Live CD.

---

