---
title: "replicating the installation to be bootable"
date: 2012-04-04
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2012-04-04
Some (very recent) variant of Ubuntu is installed on machine A.  Machine A and also Machine B are now booted into a non-Ubuntu rescue system via a USB memory stick to simplify replication (so that the installed system is not actually running when its files are copied).  Machine B is partitioned like Machine A, except /home is larger on Machine B because the disk is larger.  Partitions are formatted on Machine B using the same UUIDs from the corresponding partition on Machine A.  On Machine A, filesystems are mounted read/only at /mnt/sda.  On Machine B, filesystems are mounted read/write at /mnt/sda.  For each partition, that partition is duplicated from Machine A /mnt/sda to Machine B /mnt/sda using rsync.

I also modified /etc/udev/rules.d/70-persistent-net.rules so that interface names will not be tied to the MAC addresses, allowing the kernel interface naming to stand unchanged (since Machine A and Machine B have different MAC addresses).

**Now what else is needed to make Machine B bootable?**

I know that the GRUB image is not stored on Machine B, yet.  Is "grub-install /dev/sda" (executed from within "chroot /mnt/sda") all that is needed at this point to make Machine B bootable?  Or are there other steps?

---

### Post by papibe on 2012-04-05
Hi Skaperen.

I'm afraid rsync is not the tool for the job. rsync deals with files and it won't copy the [master boot record]("http://en.wikipedia.org/wiki/Master_boot_record"), thus not making the destination [bootable]("http://en.wikipedia.org/wiki/Booting"). I would recommend taking a look at [clonzilla]("http://clonezilla.org/").

Regards.

---

### Post by Skaperen on 2012-04-06
> **papibe said:**
> Hi Skaperen.

I'm afraid rsync is not the tool for the job. rsync deals with files and it won't copy the [master boot record]("http://en.wikipedia.org/wiki/Master_boot_record"), thus not making the destination [bootable]("http://en.wikipedia.org/wiki/Booting"). I would recommend taking a look at [clonzilla]("http://clonezilla.org/").

Regards.
Because of the size, and doing this over the network via SSH, rsync is a valuable tool.  If Clonezilla copies sectors by transmitting every sector, then it would kill my bandwidth.

But I have been doing this with rsync for years ... on Slackware.

I (have someone at that location if remote, as it usually is) boot the system using a bootable USB memory stick I make (they usually make the USB memory stick from an image I provide).  The system on that memory stick lets me log in (via a chain of SSH tunnels into the LAN the target is on).  I partition the target, format the partitions to be filesystems, mount the filesystems, and use rsync to populate the target.  Then I run extlinux to make the system bootable.  It works fine.  But it's Syslinux and Slackware, which isn't always the choice system (it's just a combination I understand well enough to make it work).

So now for Ubuntu.  Since things appear to assume GRUB is the bootloader, that's the bootloader I should use.

The question is, how do I do that LAST step for GRUB as the bootloader, since the previous steps are already done.  I do not think I need to copy the master boot record, but only make a new one on the target.  I am not asking how to redesign the process all over.  I'm asking what detail I need to do to finish this on Ubuntu with GRUB.

Why would "grub-install /dev/sda" not do this, or not be sufficient?

FYI, I do not think in terms of "this software will do everything I need to have done".  Rather, I think in terms of "to do what I need to do, what are the individual steps".  Then I consider "Now that I know what the steps are, let me see if existing software will do it for me, or do I need to write my own".  Well, right now I don't know if there are more steps beyond "grub-install /dev/sda".  That's what I am currently trying to discover.

---

### Post by Skaperen on 2012-04-09
I finally got an opportunity to try this.  The command "grub-install /dev/sda" did in fact make the system bootable.  It came up all the way to an Xubuntu login greeter.

To summarize, this is a machine on which I ran a networked rescue system booted from a USB memory stick, partitioned the hard drive, formatted the partitions into filesystems, mounted those filesystems, and copied just the files from corresponding mount points on a system that I had previously installed from DVD.

I also made sure the UUIDs were the same.  While I set the UUID during formatting, it could also be done by changing the UUID in /etc/fstab, or changing /etc/fstab to mount by device address (less flexible).

So all that is needed after that is to get grub installed.  Since the source system did already have grub installed, it was therefore also configured (that being in the files in /boot).  If you build a system without grub at first, you may need to do additional configuration steps before doing "grub-install /dev/sda".

If you want a 2nd hard drive (such as a file tree replica) to also be bootable, this might work for that, too.  I did not test this aspect.

---

### Post by Skaperen on 2012-04-09
> **papibe said:**
> Hi Skaperen.

I'm afraid rsync is not the tool for the job. rsync deals with files and it won't copy the [master boot record]("http://en.wikipedia.org/wiki/Master_boot_record"), thus not making the destination [bootable]("http://en.wikipedia.org/wiki/Booting"). I would recommend taking a look at [clonzilla]("http://clonezilla.org/").

Regards.
So, as it turns out, rsync is just fine ... as long as the additional steps to make sure the filesystem UUIDs match those in /etc/fstab, and to install grub, are done.

---

