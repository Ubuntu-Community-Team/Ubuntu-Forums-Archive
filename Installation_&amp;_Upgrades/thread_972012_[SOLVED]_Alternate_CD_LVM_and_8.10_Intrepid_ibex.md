---
title: "[SOLVED] Alternate CD LVM and 8.10 Intrepid ibex"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by jrlrocks on 2008-11-05
Hello,

I have an Intel system and had 8.04 running perfect via the alternate CD.
I disabled all "on-board" fake RAID controllers on my MOBO and raid card. (Everything was running JBOD)
Used LVM to create /boot on 1 drive and swap on the other. Partition the rest and run RAID 0 on 2 raptor drives. (69GB) Created MD0
Used LVM to run RAID 5 on 4 500GB drives and set as /home Created MD1

Here's my issue.
Downloaded IBex 8.10 Alt CD. (Wanted a fresh install) Backed up my partitions.
booted the installer. This time the partitioner saw both my raptor drives as 1 drive @ 74GB. (Not sure what RAID)
I tried the guided install for max space and received grub error 2 on reboot.
I tried the guided install for max space and LVM and received grub error 2 on reboot.
I tried to create /boot and swap "/" partitions manually on the 74GB and received error 17.

Not sure what other info you require. Or what I'm doing wrong. At present last night, I used Gpart and removed all partitions with the hopes of a clean install this morning.

Thanks,

---

### Post by jrlrocks on 2008-11-06
Bump...

Anybody have an idea how to install w/LVM raid.

---

### Post by jrlrocks on 2008-11-06
OK - so I figured out that when I ran Windows I DID use the fakeraid (Before ubuntu 8.04 about 6 months ago). I enabled it in the bios of my mobo and the drives showed that they were already in raid in the Intel raid boot screen. I disabled raid and booted the install CD. At the partition section. The installer then saw the 2 drives. That would lead me to believe that 8.10 does now support fakeraid controllers.

Now I think I have to find a way to clear the MBR as there was still something fishy when I partitioned the drives. Seems unbuntu still sees raid data on the drives. I'm trying the install. Will circle back with my findings.

[B][U]
Anyone know how to clear the Master Boot record?[/U][/B]

---

### Post by jblackthorne on 2008-11-06
Yes, Intrepid supports both "fakeraid" via dmraid or software raid via mdadm.  If you wish to raid both drives together, I HIGHLY recommend against using dmraid.  Instead, I would still with mdadm.  The good news is that this is really easy with the alternate install cd of ubuntu.

* just boot into the partition manager
* choose "advanced"
* manually create two partitions:
1. +2GB - type: 82 (swap) (you can make it up to the size of your ram if you wish)
2. +<remaining disk space) - type FD (Linux Raid Autodetect)

* duplicate the partition size and types used on the 2nd disk
* use the raid tool to select both type FD partitions to create a raid device
* Set the new raid device as file system type EXT3 with a mount of / (root), format = yes
* install from there as normal.

Yes, this is an overview. However, there are many documents on the web that go into much more detail and have screenshots.  Please do some google research and let me know if you have specific questions.

Good luck!

P.S. The install process installs grub which will correct your MBR.

---

### Post by jrlrocks on 2008-11-06
HI!

Thanks so much for your answer. So I figured out my issue on RAID for root. Now I'm trying to setup raid for my storage

4X 500GB drives.

Can I setup through LVM from the desktop?
Last time I set it up through the installer.

Thanks,
J

---

### Post by jblackthorne on 2008-11-06
> Can I setup through LVM from the desktop?
Last time I set it up through the installer.
Sure, you can create raid devices at any time.  Ubuntu ships with the Gparted tool that helps a great deal in creating partitions.  Though, Gparted does not handle raid very well.  This means that you will need to use a few command line tools to get the job done.  It is not that bad though, all you need are a few tools (outlined below)

* Install any new drives that are needed
* Use fdisk to create the new partitions as "FD (Linux Raid Autodetect)" on both disks
* Use mdadm to create a new Raid array
* Use pvcreate to create your LVM volume
* Create the file system using mkfs.ext3
* edit fstab to include your new mount

I know that is a few steps, but it really is not that difficult.  Also, there are already a number of fantastic resources that give step-by-step details on how to complete this task.  Google "software raid howto" a bit and you will find a great deal.  For example:

[https://help.ubuntu.com/community/Installation/RAID1+LVM](https://help.ubuntu.com/community/Installation/RAID1+LVM)

Just browse around a bit.  The key thing to keep in mind is:

* use mdadm and NOT dmraid

If you run into trouble while installing your array, feel free to post further questions.  Good luck

---

### Post by jrlrocks on 2008-11-07
Awesome! Second time I've installed ubuntu!

The more I play with it. Although frustrating as I don't know many commands and have to research. The more I like it.

---

