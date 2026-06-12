---
title: "How to use brtfs for a Ubuntu install?"
date: 2014-04-01
forum: Installation &amp; Upgrades
---

### Post by cdysthe on 2014-04-01
Hi,

For years the way I have installed Ubuntu on my laptops has been to create a /, a  /home and a swap partition. I've installed Ubuntu on / using the Ubuntu installer and kept /home untouched (using the "something else" option in the installer). When I then want to do a fresh install I clean out /home by deleting everything except my data and install the OS on a formatted / again using the same user name for my account. I then have all my data available in /home immediately. 

I now have a secondary laptop I would like to dedicate to trying out btrfs. I know that installing with the same disk layout won't get me the full benefits of using btrfs. So how should I partition the disk as far as partitions, volumes, subvolumes and swap so I can go the same route when I want to update (or switch distro) where I keep all data in /home and install the OS?

---

### Post by grahammechanical on 2014-04-01
> [COLOR=#000000] I know that installing with the same disk layout won't get me the full benefits of using btrfs. [/COLOR]

I do not know this at all. When I have installed Ubuntu on a btrfs file system. I chose the Something Else option and selected the partition and then clicked Change. In the Use As panel I selected btrfs from the menu.

There is a little bit more to do to get a successful install. Make sure that there is a minimum of 1MB of unallocated space at the front to the hard disk otherwise the install will fail with an unable to install Grub message.

The partitioning of the hard disk can stay the same. You may not want to have the /home partition on btfs because reverting a snapshot will revert all the changes to your data. Although you may want some of the other benefits of BTRFS.

All the sub-volume etc., stuff is put under / folder. 

> [COLOR=#333333][FONT=Ubuntu]Subvolumes are created below the top of the btrfs tree as needed, e.g. for **/** and **/home**, it creates subvolumes named **@** and **@home**. This means that specific options are needed in order to mount the subvolumes, instead of the default btrfs tree top:[/FONT][/COLOR]

[LIST]
[*=left][FONT=inherit]The **@** subvolume is mounted to **/** using the kernel boot option [FONT=inherit]rootflags=subvol=@[/FONT][/FONT]
[*=left][FONT=inherit]The **@home** subvolume (if it is used), is mounted via the mount option [FONT=inherit]subvol=@home[/FONT] in fstab.[/FONT]
[/LIST]


> [COLOR=#333333][FONT=Ubuntu]As of 11.04, it is possible to use only btrfs file systems with the caveat that grub **'MUST NOT**' be installed to the boot sector of the btrfs volume containing /boot. See also [Ubuntu Grub2 Bug 757446]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/757446") and [Ubuntu Grub2 Bug 759772]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/759772"). You must install it to either the parent (sda rather than sda1; MBR/Reserved Sectors) **'OR**' use a dedicated /boot partition as described in the forum post below.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]When installing Ubuntu in one large btrfs-Partition without an extra boot-partition, take care to keep about 1 Mib space free at the beginning of the disk. This is possible using the partition manager in the Ubuntu installer. When there is not this space, the installer fails at the end when trying to install Grub![/FONT][/COLOR]


[https://help.ubuntu.com/community/btrfs](https://help.ubuntu.com/community/btrfs)

When I experimented with BTRFS I did not use a separate /home partition because I keep all my data on a data partition. I found btrfs not so useful on a home desktop system because we lack a decent GUI snapshot manager.  The taking of snapshots and the reverting of them has to be done in a terminal. It can be done in Recovery mode. 

If we install apt-snapshot then a snapshot will be taken every time we update Ubuntu. In Recovery mode if we put the file system into read/write mode by running Network (for example) we get a Revert apt-snapshots option in the Recovery menu.

Regards.

---

### Post by cdysthe on 2014-04-02
Thank you! That was very helpful. The last question I have in this regard is whether I can convert my current ext4 /home partition to btrfs and use it in the new install?

---

