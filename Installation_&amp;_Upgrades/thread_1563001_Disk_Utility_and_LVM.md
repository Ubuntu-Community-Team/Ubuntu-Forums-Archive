---
title: "Disk Utility and LVM"
date: 2010-08-28
forum: Installation &amp; Upgrades
---

### Post by TennTux on 2010-08-28
Hi, Either I don't understand "Disk Utility" or it's not as useful as I was hoping.

When I use this utility it shows a "SATA Host Adapter" with 3 disk drives sda, sdb and sdc as expected. It also shows my CD/DVD, not relevent to my questions. Currently I only use sda. I have plans for sdb / sdc but their presence only brings my confusion into focus.

sda is a 500 GB drive.

The graphic shows a "255 MB ext2" section on the left (sda1) Bootable It also shows an "Extended" "500 GB" section on the right top (sda2) I assume
this is 255 MB less than 500 GB. And finally it shows a "500 GB LVM2 Physical Volume" "500 GB" on the right bottom (sda5)

In the same list as the "SATA Host Adapter" is a "Peripheral Devices" entry with a "Floppy Drive" and a "500 GB Hard Disk" that I believe is my sdb & sdc as a RAID. Then there are 2 more entries "192 GB Hard Drive" Ext4 mounted as "/" and "8.1 GB Hard Drive" Swap Space.

Now I suspect that I am suppose to interpet all this as "255 MB ext2" and "Extended 500 GB" are primary partitions with the first being the boot partition. And that "Extended 500 GB" has within it 1 sub partion "500 GB LVM2 Physical Volume". And then the "500 GB LVM2 Physical Volumne" is further broken down into "192 GB Hard Drive" and "8.1 GB Hard Drive".

Part of my confusion is how do I know this last point? Once I partition my RAID I assume it will provide additional entries in the "Peripheral Devices" and how do I know which ones are on sda vs sdb/sdc? The crux of my question is the "Peripheral Devices" do not specify what drive they are part of. Each logical drive has a name but the drives under the "SATA Host Adapter" do not have those names.

Also I am using 192 GB + 8.1 GB of 500 GB. Which device do I partition to allocate the remaining 299.9 GB?

Back in Dapper Drake there was a similar utility that I found more understandable, though I suspect my problem is not the utility but rather the Logical Volume Manager that is abstracting stuff. But it did seem that the old utility showed the parts of the volumes that where not used so you could partition and format them.

I have been trying to use the new and spiffy GUI tool. Would I be better off using the old tried and true command-line tools? If so, which ones should I be using to get the info I'm looking for and which ones to partition? df? gparted? fdisk?

---

### Post by TennTux on 2010-09-01
Am I asking this question in the wrong forum? Or did I make a mistake by installing LVM (Logical Volume Manager)? Or is this just too advanced a question for this type of forum?

---

### Post by TennTux on 2010-09-01
Found a partial answer through documentation.

```
sudo lvm pvdisplay -m
sudo lvm lvdisplay -m
```

These will provide info with regards to logical and physical volumes and the mappings between them.

As for creating a new logical volume within a volume group the following worked for me.

```
sudo lvm lvcreate -L 150G -n partitionName volumeName
```

From here formatting and mounting should be doable with either lvm or Disk Utility.

While it would have been nice for Disk Utility to have better support for LVM my biggest hurdle was figuring out that I needed to use the lvm command. Once I figured that out I was able to read the doc(s).

---

