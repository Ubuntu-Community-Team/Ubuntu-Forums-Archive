---
title: "Software RAID (Desktop version)"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by TheGameAh on 2007-12-18
I've searched high and low.  Found plenty of docs on setting up software RAID on Ubuntu server, but not desktop.

Using the latest version (64bit), trying to setup a RAID 1 between 2 disks.  However, no option for "RAID" is in the install setup partitioner.  Any tricks to get this working?

---

### Post by finesse on 2007-12-18
I also would like to know how to do this. I was dual booting with WinXP and I couldnt see my motherboards fakeraid in Ubuntu to mount it.. As I would like to install Ubuntu to the raid I need to be able to see it.

I believe the problem is related to my motherboard because when using Windows I can't use my CDROM and in Ubuntu my CDROM works but my raid doesn't - this seems to be a bug with the controller which is a 2port SATA (set to raid) and 1 IDE port which my CDROM is connected to.

Im hoping when I set the 2 SATA ports to normal (non-raid) I can get both working but need to use software raid.

Im assuming its something simple like using the Live Install CD and running a software raid program before running the install. As I havn't used linux much I know not how to do this.

---

### Post by jayson.rowe on 2007-12-18
In order to set up a Software Raid, you need to install from the Alternate CD rather than the Desktop Live CD.

You will have the option while partitioning your disks to choos "Linux RAID" as the partition type, and then you can create your RAID arrays.

Remember, if you want / to be on a raid, you will have to create a small /boot partition - I usually do about 128 MB and use the EXT2 file system.

---

### Post by TheGameAh on 2007-12-18
Ah.  Figures that's all it is.  :)  Downloading Alternate now.

A little new at software Raids.  If a drive fails, will the second drive boot up fine, like in hardware raid?  Or do you have to do funny tricks like installing Grub on both drives?

---

### Post by jayson.rowe on 2007-12-18
No funny tricks - just make sure to create a /boot partition that is not on the RAID

---

### Post by psusi on 2007-12-18
Yes, you end up having to use funny tricks most of the time.  You will need to install grub to both disks on a non raid partition, and if the primary drive is the one that fails, the system won't be able to  boot until you either tell the bios to boot from the other one, or yank out the failed drive causing the second one to become primary.

For more information on hardware fakeraid, see [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto)

---

### Post by jayson.rowe on 2007-12-18
I've never had to do any funny business on my desktop...

Simply made a boot partition (not on the RAID) and told my BIOS which hard drive to boot (the one GRUB installed to).

---

### Post by jayson.rowe on 2007-12-18
Let me clarify a little more...

First - boot from the alt. CD.

let's say you have two 250 GB HDD's.

too start with
On the first hard drive create a 128MB ext2 partition for /boot
then create a 896MB Partition for swap.

On the second hard drive create a 1GB Swap.

Now on the first hard drive create a 10GB Linux Raid partition and a 239GB Linux RAID Partition (md0 and md1 respectively.)

On the Second drive do a 10GB Linux RAID partition and a 239GB Linux RAID Partition.

Go into create RAID (will work for RAID 0 or 1, let's say we want to stripe).
Create a RAID device, and select the 2 10GB Partitions.
go back
Create a RAID device, and select the 2 239GB Partitions.

Now go back to the main partition set up and you should see a 20GB Raid device and a 478GB RAID Device.

Mount the 20GB as / and format it with whatever filesystem you want.
Mount the 478 as /home and format it with whatever filesystem you want.

Proceed with install and enjoy the speed.

I can not tell you how many times I've done the exact set up. It works, it's simple. When the installer does GRUB, note which hard drive (should be sda by default) and make sure the BIOS is set to boot from that hard drive.

---

### Post by psusi on 2007-12-19
> **jayson.rowe said:**
> Let me clarify a little more...

First - boot from the alt. CD.

let's say you have two 250 GB HDD's.

too start with
On the first hard drive create a 128MB ext2 partition for /boot
then create a 896MB Partition for swap.

On the second hard drive create a 1GB Swap.

Now on the first hard drive create a 10GB Linux Raid partition and a 239GB Linux RAID Partition (md0 and md1 respectively.)

On the Second drive do a 10GB Linux RAID partition and a 239GB Linux RAID Partition.

Go into create RAID (will work for RAID 0 or 1, let's say we want to stripe).
Create a RAID device, and select the 2 10GB Partitions.
go back
Create a RAID device, and select the 2 239GB Partitions.

Now go back to the main partition set up and you should see a 20GB Raid device and a 478GB RAID Device.

Mount the 20GB as / and format it with whatever filesystem you want.
Mount the 478 as /home and format it with whatever filesystem you want.

Proceed with install and enjoy the speed.

I can not tell you how many times I've done the exact set up. It works, it's simple. When the installer does GRUB, note which hard drive (should be sda by default) and make sure the BIOS is set to boot from that hard drive.

And if sda fails your system becomes unbootable.

---

### Post by AusIV4 on 2007-12-19
Personally, I have one 40GB disk that serves as my root file system (including boot), and three 250 GB drives bound together with RAID 5 that I use as my /home file system. I also have an LVM logical volume layered on top of the RAID 5, so if I wanted to I could break it up into separate partitions.

Now, for a long time I didn't have 3 x 250 GB drives. Instead, I had 1x160 and 2x250. So I partitioned off 160 sections of my 250 GB drives, and created a raid 5 with 3x160 sections, and a RAID 1 with the remaining 90 GB sections and I used LVM to tie them together. I had all sorts of problems with this setup. My devices were frequently becoming degraded and I'd have to spend a lot of time waiting for them to be repaired.

My advice would be if you have two devices, make a separate boot partition and swap partitions as suggested, but then, rather than make two RAIDs from 2 disks, make 1 raid from them, then segment it using LVM. This way you won't be tied to a specific size. If you want to add disks later, you can add them to the volume group and expand the logical volume. If you decide your root partition doesn't need to be 20 GB, you can take easily take some space from it and give it to your other device.

Take a look at the [linux documentation project ]("http://tldp.org") for details on how to use LVM.

Also, if you're just doing RAID 1, I'm not sure you need a separate boot partition. The two drives are mirrors of each other, so the data isn't striped like in the other RAIDs. Since both devices would pretty much be a readable drive, I think you should be able to point to either one as your boot partition. (Note that this won't work with my LVM suggestion)

---

### Post by psusi on 2007-12-19
Note that you can expand partitions just fine without LVM.

---

### Post by jayson.rowe on 2007-12-19
> **psusi said:**
> And if sda fails your system becomes unbootable.

I was only using Raid0 as an example.

I run this way on my Desktop - I have no problems re-installing that system. I also have 2 500GB Drives that are mirrored, and store my critical data.

All my desktop really does is serve as a VMware Host server and a File server.

I use the mirrored 478GB partition formatted w/ JFS for running "Live" virtuals, but I have them backing up to the mirror for safety.

Literally there is nothing installed on that system other than what installs off the CD, with the exception of VMware server - I can re-install that system and be right back where I was in less than an hour.

I was simply giving my example as I was having trouble describing it other ways.

---

