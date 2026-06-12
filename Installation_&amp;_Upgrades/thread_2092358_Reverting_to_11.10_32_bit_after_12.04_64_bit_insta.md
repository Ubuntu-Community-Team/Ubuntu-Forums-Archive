---
title: "Reverting to 11.10 32 bit after 12.04 64 bit installed &quot;along side&quot;"
date: 2012-12-07
forum: Installation &amp; Upgrades
---

### Post by upandacross on 2012-12-07
I'm doing some large data set processing and need to go to 64 bit. Figuring 12.04 has been out long enough to be solid, I installed 12.04 64 bit "along side" 11.10 into a separate partition. After the normal "nomodeset" problem with the nouveau driver and my NVIDIA card, it looks like 12.04 isn't as stable as I hoped (e.g. compiz manager crashed right away and even after reinstall, Alt-Tab still doesn't switch between programs). I just don't have the time to futz with 12.04 - I need to get back to my data set.

So, I want to back off 12.04 64 bit and install 11.10 64 bit "along side" the 32 bit version where I've been working. The intent would be to replace the 12.04 partition with the new 11.10 partition.

Two Question: 

[LIST=1]
[*]If I reformat the 12.04 partition, will that confuse GRUB? Do I need to make some changes to a boot record? /etc grub files? others?
[*]How **exactly** do I make sure the new 11.10 64 bit is installed in the new partition (i.e. "along side" the existing 11.10 32 bit)? ):P
[/LIST]

---

### Post by darkod on 2012-12-07
Unless you delete the 12.04 partition(s), it will never install in its place. The installer will never overwrite any partition unless directly told to.

The best way to make sure what goes where, including the bootloader, is to use the manual partitiong (Something Else). When it lists the partitions, select the 12.04 root partition, hit the Change button, and select the Use As ext4 and mount point /. That will tell the installer to use that partition as the 11.10 /.

You can use the same swap partition that already exists on the disk.

For bootloader destination select the MBR of the disk, like /dev/sda for example. Don't put it onto a partition.

That should be it.

If you insist on using the auto install method, you will need to first delete the 12.04 partitions so that there is unallocated space on the disk. The auto method uses the largest available unallocated space.

---

### Post by upandacross on 2012-12-07
Darkod,

Thanks for shedding light on this. \\:D/

---

### Post by darkod on 2012-12-07
I forgot to mention, when you select the 12.04 root partition to use as root for 11.10, also think the format box. Because if the partition is already ext4 and you tell it to use it as ext4, it will not get formatted by default. You need to tell it to format it so that all 12.04 files are deleted.

---

### Post by upandacross on 2012-12-07
For those who may follow, GRUB "remembers" that a partition was bootable in the past, so it you just reformat it and reboot, you will get "Error: No Such Device ........" and a GRUB Rescue> prompt. Not fun.

Here's how I recovered: just so happened to have a Ubuntu live boot USB. Booted from it, started a terminal, and did the following:

sudo apt-add-repository ppa yannubuntu / boot-repair
sudo apt-get update
sudo apt-get install boot-repair && boot-repair

You get a GUI - I let it do it's thing ("the recommended" actions)
and life is good again. :roll:

---

