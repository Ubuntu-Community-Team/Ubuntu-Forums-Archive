---
title: "Kubuntu installation w/RAID1 results in GRUB Error 17?"
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by josh2112 on 2008-11-15
I am trying to install Kubuntu with a RAID1 array based on the excellent instructions at [http://users.piuha.net/martti/comp/ubuntu/en/raid.html]("http://users.piuha.net/martti/comp/ubuntu/en/raid.html").

I have two 750 GB disks and I want to partition them like so:

20 GB  - ext3 - root (mount point "/")
329 GB - ext3 - home (mount point "/home")
400 GB - xfs  - mythtv recordings (mount point "/mythtv-recordings")
1 GB - swap

The first three partitions are going to be RAID1. The swap I don't care about, each disk can have it's own swap as far as I'm concerned.

I'm using Kubuntu 8.04.1 Alternate for amd64.  I create the four partitions identically on each disk, marking the first 3 as "physical volume for RAID", and making sure the first partition on each disk is marked bootable.  I then create the RAID arrays (interestingly enough, the installer RAIDed the first two partitions automatically for me but I had to create the xfs RAID array manually).

Everything looks fine, the install finishes, then when I reboot I'm presented with a GRUB error 17 - cannot mount the partition.  I see that the GRUB entry the installer set up is setting the root to "/dev/md0".  Setting it to "/dev/sda" doesn't help.

I've spent all day on this, tried it 2 different ways, done 4 different installs, and I'm still not getting anywhere. Why is this so hard?  And what is the easiest way to accomplish what I want done?  Would it be easier to just install the system on one disk, then make a RAID array later?  And if so, how do I do that??

Thanks,
  Josh

---

### Post by josh2112 on 2008-12-02
If anyone's interested, I have gotten around this... although I still don't know what caused it in the first place.

In the Kubuntu Alternate installer, I created all the partitions but only created ONE raid1 array - 20GB ext3 mounted as '/' - and installed to that.  After a successful boot up, I created the other two raid1 arrays manually using mdadm.

This wasn't quite as easy as it sounds, since /home had been created under root, so I had to move the contents over to the second raid1 array after creating it... and of course, add /etc/fstab entries for both of the new arrays.

Still don't know why the installer had such problems with creating all three raid1 arrays at once...

---

