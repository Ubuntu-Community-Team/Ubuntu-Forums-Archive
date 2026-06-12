---
title: "Partitions for installation on external hard drive"
date: 2020-07-31
forum: Installation &amp; Upgrades
---

### Post by garlvz on 2020-07-31
Hello, I want to install ubuntu on an external SSD (240 GB) to use it on different PCs.
I watched different tutorials and some people only partition the hard drive in root and swap, while others add also the home partition.
What would be the best option if I wanted to upgrade the OS and the softwares without making backups?
NOTE: The guest will be disabled so safety of the root shouldn't be a problem

---

### Post by oldfred on 2020-07-31
UEFI or BIOS systems.
Difficult to be both.

If UEFI, use gpt partitioning and partition in advance with an ESP - efi system partition.
I do not use encryption, but many suggest it for portable devices. But then that is an LVM type install.

I like to keep / (root) smaller like 30GB and use larger data partitions. I keep /home inside / as /home without any data is much less than 1GB. The advantage of /home is then installer adds mount to fstab and sets ownership & permissions for use. If data you have to create it separately and do all the mount & settings manually. If newer user having just / would be ok with your 240GB drive, but any larger drive, I would not want a root that large.

New versions of Ubuntu now use a swap file, so swap partition not required, but will be used if found.

Ubuntu's Ubiquity installer in UEFI mode has a very old bug where it only installs grub2' boot loader files into the first ESP, normally the internal drive. Some disconnect drives or disable in UEFI. Some say from live installer removing boot flag from internal drive's ESP and installing works to get it to install to correct ESP on external drive. Just be sure to reset flags on internal ESP before rebooting.

Posted work around to manually unmount & mount correct ESP during install #23 & #26
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

---

### Post by pbear42 on 2020-08-01
> **garlvz said:**
> 
What would be the best option if I wanted to upgrade the OS and the softwares without making backups?
Surely you don't mean to say you don't back up your data files.  And, if you do, this question exaggerates the importance of partitioning.  After all, it's a pretty simple matter to copy the data files back in every two years (the interval between LTS versions).  

Meanwhile, once you start splitting up the drive, you have to decide how much room to give root.  As oldfred says, 30 GB is plenty for a normal installation (indeed, includes a generous but reasonable buffer).  OTOH, might not be enough if you're going to install a bunch of Snaps (so you can always have the latest software releases).  And there are other issues.  My general advice is, use a single root partition for your first system, then something more elaborate for the second.  When that rolls around, you'll have a better idea how the system works, how you use it, and what partition scheme fits you best.

It's a topic over which reasonable minds differ.  Just my $0.02's worth.

---

### Post by pbear42 on 2020-08-01
> **oldfred said:**
> UEFI or BIOS systems.
Difficult to be both.
FWIW, there's an obscure trick for doing this, which turns out to be not difficult.  Found here on the [Forum]("https://ubuntuforums.org/showthread.php?t=2213631&p=13391873#post13391873"), as it happens, but never caught on.  In a nutshell, format the drive GPT, with both EFI and BIOS boot partitions.  Install first in BIOS mode, then boot in BIOS and install the UEFI boot loader.  Avoids the bug and nothing needs to be switched on the host computer.  Whatever boot mode is set in the firmware gets used by the USB drive (assuming, of course, USB is first on the list).  There's a way to do the installation the other way round (install in UEFI, then add the BIOS boot loader), but it's a bit more complicated (requires chroot).

Update:  After I posted that, I realized I hadn't tested Reverse Hybrid (the second procedure) with Ubuntu 20.04.  Turns out, the problem which caused me to need to use chroot has been solved, so an ordinary grub-install command (specifying --target=i386-pc) will work to add BIOS boot.  So, the second procedure is now actually a little easier than the first, and neither is difficult (imho).

---

