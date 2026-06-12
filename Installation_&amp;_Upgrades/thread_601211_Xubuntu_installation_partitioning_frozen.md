---
title: "Xubuntu installation partitioning frozen"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by popformula on 2007-11-03
I'm in the process of installing Xubuntu 7.10 on my friend's laptop, a Toshiba Satellite Pro with 240MB RAM and a 1.7GHz Intel processor. There's already a Windows XP installation taking up 30GB or so of the 40GB hard drive, which I want to leave intact.

I booted off the livecd and ran the installer application on the desktop, chose the language and time zone with no problem.

When it came to repartition the hard drive, I chose "guided resize and install on freed space" and set the slider at 93% which said 32.2GB, thinking this would leave about 7GB for the /swap and the Xubuntu file system.

I clicked next and it told me the changes would have to be applied before we could continue. I clicked OK, the dialog disappeared leaving the window with guided/manual options and the slider, but at this point the mouse and keyboard stopped responding, no status bar or progress window appeared. It's been like that for an hour, now. There doesn't seem to be any hard drive activity, and the CD's not spun up.

It would be a real pain if the disk partitioner scrambled the XP partition. Is my best bet just to wait it out? Why is there no status bar? If I restart, do I risk losing the data on the XP partition? Is it normal for it to take this long?

Thanks!

Joe

---

### Post by fdv1 on 2007-11-03
You told it to take 93% of the hard drive, not to allocate 7% for swap.

No, it should not take this long. **Something is wrong.** Although I cannot say for certain, probably your XP is ok, and it might boot allright since install hasn't gotten to installing a boot manager.

I f'ing HATE the install routines from the live CD, so here's what I do... Here's how I saved my wits and my Windows partition:

1. Download and burn an alternative install CD. Never mind this live CD nonsense.
2. Use Partition Magic or Partition Logic or Acronis or Paragon Hard Disk Manager to create a new partition.
3. Go ahead and format that new partition as ext2. No need to create the swap.
3a. So your primary hard drive has 2 partitions, and it's split at about the 50% point, or halfway: NTFS for Windows XP, and ext2 for Linux to use, and to create a swap within it (again, the OS will do that, not you).
4. Boot with the alternative install CD now.
5. Edit partitions manually, and tell the installer what's what. In other words, point it to the ext2. It should take care of the rest without serious problems.

If this is any way confusing... Don't do it! Go back and use the live CD and specify 50% and hope for the best. Better to have something messed up to play on than to lose your data!

---

### Post by popformula on 2007-11-03
I booted back into Windows fine, GRUB was installed and gave me the option of Ubuntu or Windows. I've downloaded PartitionMagic. I'm currently downloading the Alternate CD on my laptop, too.

Although the disk has 7.5GB free space, PartitionMagic only gives the option of creating a new partiton up to 1.7GB in size. I'm defragmenting the disk at the moment, thinking this might allow me to create a bigger partition (I want to give Xubuntu about 5GB).

Why should I use ext2 rather than ext3? Any ideas why partition magic reads the disk as 7.5GB free but limits me to a partiton or 1.7GB?

Thanks for your help, although I've only been using Ubuntu myself for a few months, I think I feel brave enough to give the alternate CD a try...

---

### Post by popformula on 2007-11-03
In case anyone's interested, I have an idea about the bug.

Although the NTFS partition was reported as having 7.5GB free, the livecd crashed whenever it tried to resize the partition, during the disk configuration setup before the actual installation begins. I was trying to shrink the NTFS by 5GB to make room for Xubuntu.

When I booted back into Windows, PartitionMagic would only let me shrink it by 1.7GB, with no explanation given. I burnt a gparted livecd and used that to try and shrink the partition by 5GB, it started but gave me an error during the simulation. I tried shrinking by 1.7 and it completed successfully. 1.7GB wasn't quite enough space, though.

I booted back into Windows and defragged again, then ran the gparted livecd and was able to shrink about another 1.7GB off the partiton.

I then booted the Xubuntu livecd and formatted the free space using the graphical installer (500mb SWAP, 3GB root) and tried to complete the installation. It hung up again, though. This time I was able to get to the end of setup; once I clicked "Install" it tried to load the partition manager and froze.

In the meanwhile I'd been downloading and burning an alternate cd; I popped this in and had a working installation within 45 minutes.

So it seems that 1) PartitionMagic was able to identify only 1.7gb could be shrunk, and told me so. 2) gparted wasn't able to tell beforehand, but during the simulation it realised and gave me and error message. 3) Xubuntu livecd tried to go ahead with the resize and prompty locked up.

Still, all's well that ends well.

As an aside, it would have been great to be able to configure PPPoE during the install; the pppoeconf, although fantastic, is not at all obvious once you're up and running.

Is it worth my filing any kind of bug report about these problems? If so, where would I do it?

---

