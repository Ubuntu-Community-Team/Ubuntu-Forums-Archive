---
title: "More on &quot;Waiting for root file system&quot; - how do you specify filesystem type in grub?"
date: 2006-06-12
forum: Installation &amp; Upgrades
---

### Post by grandpa-geek on 2006-06-12
I posted an earlier thread about trying to boot Ubuntu from the boot partition set up by my primary Fedora Core 5 installation, where Ubuntu is installed (via the alternate install iso) on an LVM partition.  I got no responses to that thread, but had seen a "Waiting for root file system" message and decided to follow up on suggestions related to that.

This isn't exactly the same problem as other people are having with the same "Waiting for root file system" message, but the problems are likely to be related.

I had tried multiple things to get Ubuntu to boot on my system and finally arrived at copying the Ubuntu kernel and initrd to the same /boot set up by FC5.  Ubuntu is installed on VolGroup00/LogVol03.  My grub kernel root statement is root=/dev/mapper/VolGroup00-LogVol03/.  The boot kept hanging at "Waiting for root file system".  I followed the advice of the other threads and waited.  I then got a message that /dev/mapper/VolGroup00-LogVol03/ does not exist, and the initrd brought up a shell with BusyBox.  

I had seen a mesage that four partitions were now active in VolGroup00, so I figured something was working up to a point.

I looked at the /dev of the initrd, and there were /dev/mapper/VolGroup00-LogVol03 and /dev/VolGroup00/LogVol03.  So the root filesystem is really there!  I then created a mount point /mnt/ubuntu and tried to mount the filesystem.  It kept telling me the filesystem didn't exist until I tried "mount -t ext3 /dev/mapper/VolGroup00-LogVol03 /mnt/ubuntu" and  it mounted.  So it isn't detecting the filesystem type, needs to be told what it is, and is giving a misleading message that the root filesystem simply doesn't exist.

Now the question is how do I include the filesystem type of "ext3" in the "root=" statement?   That seems to be what is keeping the root filesystem from being mounted and Ubuntu booted.

I googled around and found a "rootfstype" parameter in a kernel discussion, but that was a proposal around 2001 and it wasn't clear that it had been accepted or what it is now.

Can anybody tell me how to specify a filesystem type of ext3 in my root= statement in grub for the kernel?

---

