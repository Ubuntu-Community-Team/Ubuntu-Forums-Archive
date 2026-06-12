---
title: "partition issues, dual boot issues"
date: 2010-01-16
forum: Installation &amp; Upgrades
---

### Post by arnicainthemembrane on 2010-01-16
I have winXP dual booted on my computer with Ubuntu 9.1. The problem is, during the installation process I had to interrupt what the computer was doing and later attempt to re install. As a result, When I start up the computer I'm given not just the option to start up Ubuntu 9.10 by default, but also Ubuntu Recovery mode, as well as Windows. I immediately downloaded Gparted and the attached image shows what my hard drive looks like. 

I'm wondering, how can I

1. Figure out which drives are actually being used for Ubuntu right now?
2. Clear out format and consolidate sda6 and sda7 so I can use them for storage?

thanks...

---

### Post by -kg- on 2010-01-16
Your screenshot of GPartEd tells me that you have (perhaps *almost*) installed Ubuntu twice.  There are two swap partitions, and you have two other partitions which are not marked with a mount point.  One of these is likely the original root partition (I would say the one with the least amount of data in it).

What you want to do is boot to the Live CD then check three of the partitions.  First check your actual root partition (sda8 ) and notice what files you see in there.  Likely you will only need a cursory glance.

Next check sda6 (the one I'm betting is your original root partition) and see if the files in that match (approximately) the files on your current root partition.  If they do, check sda7 and see if your stored data files are on that partition.  I notice that there is quite a bit of data in that partition, so it's very likely that that is your data partition with your data on it.

Well, I was typing up some instructions but had to start over.  I was going to tell you to delete some partitions and expand the other relevant partitions, then I noticed that your current root partition is sda8.  When you delete partitions (and sometimes when you resize them) the partition table is changed and you will be unable to boot to the hard drive until you do a bunch of extra work on GRUB.

If the installation you have is relatively new, I would opt for a re-installation.  Back up your important data from the partition that you found it on.  There is the possibility of data loss with *any* partitioning operation.

Then boot to the Live CD desktop and launch GPartEd (I will assume you already know how to do this).  Delete sda8, both of the swap partitions, and whichever of the other partitions you found to contain the root files from the original installation.  You should be left with sda1 (your Windows partition), your sda3 (assumably your Windows recovery partition), sda2 (the Extended partition), and sda(x) (probably sda7, but whichever you found to contain your data).

Next you should resize your data partition to the desired size.  This will take a while (probably *quite a while*).  Alternatively, if you have a good backup of the data from that partition, you can just delete this partition as well, then create a new partition at the desired size.  You can then copy the data back on the partition at leisure.

Once all this is done, you do the new installation.  When it comes down to the partitioning section, choose the "Install to largest contiguous free space" option.  Of course, if you're confident in what you're doing at this stage, you can also choose manual partitioning and specify your partitions and their mount points manually.

Then the installation goes on, the new partitions are created and you're in like flint.  All you have to do is do your updates, install the software you need from Synaptic, and you're in.

What happened is that the original installation was interrupted after the partitioner already had made the partitions for it.  The first thing you needed to do when you started the second installation would have been to check your hard drive to make sure that no partitions were created, and if they were, you would need to delete those partitions immediately before you started installing.

If you need further information on partitioning, read on the pages linked to in my signature, and if you need further help, just post back and I'll be more than happy to help.

---

### Post by mringer on 2010-01-16
> **arnicainthemembrane said:**
> [cut]

I'm wondering, how can I

1. Figure out which drives are actually being used for Ubuntu right now?



I would suggest: 

mount

should tell you which disk partitions are in use as file systems, and

swapon -s

ditto swap space. If you are using grub to boot, then its config file

/boot/grub/menu.lst

should tell you which partition(s) are used when you boot Windows.
Hope this helps, I cannot offer advice on your Q2.

---

### Post by arnicainthemembrane on 2010-01-16
I followed all the instructions and gparted gives me the attatched readout.
 Presently mount gives me:

/dev/sda6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda7 on /home type ext4 (rw)
gvfs-fuse-daemon on /home/arnica/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=arnica)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
 
... which is, unfortunately, utter gibberish to me. I did leave part of the drive unused, and would like to figure out how to use gparted to allocate that space for memory.

Thanks for the advice, if someone could point me to a resource teaching how to make sense of what a mount command produces...

---

### Post by mringer on 2010-01-17
I believe that the relevant lines of your mount output are these:

> **arnicainthemembrane said:**
> 
[cut]

/dev/sda6 on / type ext4 (rw,errors=remount-ro)
/dev/sda7 on /home type ext4 (rw)



which means that UB is using sda6 & sda7 for files. I would venture to
suggest that you still need to see what partition(s) are being used 
by Windows and for swap. On reflection, I dont like what I suggested 
for Windows. It might be better to start Windows; click on My Computer;
right-click on the C: drive, click Properties; see what size the
drive is; and compare with your partition table. Ditto for the D: 
drive if present. Best of luck, Mark

---

