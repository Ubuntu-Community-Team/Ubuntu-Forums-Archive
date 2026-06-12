---
title: "Lucid Lynx can't find files to boot"
date: 2010-07-15
forum: Installation &amp; Upgrades
---

### Post by Alexis Phoenix on 2010-07-15
I upgraded Karmic to Lucid 2 days ago, rebooted, and the system (a Dell Inspiron 1501 AMD 64 laptop) hung just after running fsck.  The last message was from ureadahead, error 4, 3 times, which means AFAICT it couldn't find any files to boot on my 3 partitions, /, swap and /home.  Before that there are some warnings about changes to udev affecting user defined devices, and upgrading my applications to use ext4 (the fs is ext3).
 
I've looked at other people's similar problems, and it appears that I am alone in this.  I'm using Syslinux rescue to investigate my system and can't find anything obviously wrong.  Nothing is being written to the log files - the last thing I have is the main upgrade log.  I can get some kind of info with magic sysrq, but don't understand it since I'm not a programmer.

I ran fsck from Syslinux and it ran fine.  My fstab looks fine too - no errors to suggest otherwise either.

It looks like the boot process is getting lost when the main startup is supposed to run - hence I can't even get into single user mode.

I hope someone can help me - I really, really don't want to have to wipe my / and do a fresh intall!

Many thanks
Alexis

---

### Post by dabl on 2010-07-15
Are you sure that fsck completed successfully?  Does your syslinux handle the ext4 filesystem?  If you're not certain, I would advise making a Parted Magic Live CD, and use that to fsck the hard drive again, and make sure it completes with no errors, then try a reboot.

Since the Parted Magic CD also has a GUI tool for checking the hard drive (SMART), you might as well run that too, and make sure the hard drive is up to spec.

---

### Post by Alexis Phoenix on 2010-07-16
Hmmm, 
```
root@sysresccd /root % e2fsck -p /dev/sda5
/dev/sda5: clean, 352684/1414272 files, 2384189/2827432 blocks
root@sysresccd /root % e2fsck -f /dev/sda5
e2fsck 1.41.8 (11-July-2009)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda5: 352684/1414272 files (5.7% non-contiguous), 2384189/2827432 blocks
```
I think I must have been a little misleading in my original post.  I'm not using ext4 - I just had some warnings about upgrading applications to use it.  As you probably know, ext3 can't be changed to ext4 without a reformat - unlike changing ext2 to ext3.  So since this is an upgrade it's just not possible.

I think the boot process is falling down the gap where the initrd leaves off and the kernel takes over, presumably when it's suposed to be mounting /dev/sda5 on /.  Unfortunately I don't know enough about the boot process to identify this point and what's supposed to happen. I guess I'm just going to have to do lots of reading... 

I suppose I could try building a small kernel with everything needed built in but I don't really want to...

Is there some way to log the boot messages from this early stage?  I have an ancient printer that will do the job but have to use a usb to parallel adapter and I don't think the usb connection will be recognised this early on.

Cheers
Alexis

---

### Post by Alexis Phoenix on 2010-07-22
*bump*
I found out how to chroot into Lucid using the Gentoo based Syslinux rescue cd so I was able to run 
apt-get update
apt-get upgrade
from there.  I had one sucessful boot following this, after which it gone back to not working.  I tried disabling Plymouth as some have suggested, but no luck there.

Any ideas?  Anyone?  If I can't fix this I might just switch to another distro with less bells & whistles...  Arch Linux looks nice...

Alexis

---

