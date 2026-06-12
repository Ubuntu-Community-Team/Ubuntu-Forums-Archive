---
title: "RAID1 repartitioning help"
date: 2011-08-01
forum: Installation &amp; Upgrades
---

### Post by packerac on 2011-08-01
Hi there,

I am very new to Ubuntu. I am trying to set up a system which I will use as a game-server for me and my friends.

I just installed Ubuntu server edition to my computer (brand new, no OS) and finished installation. In the terminal I used apt-get ubuntu-desktop to install a desktop interface.

In my rig, I have two 500GB HDDs. I set them up through my computer BIOS as RAID1 drives, yet as I understand I still need to configure the Ubuntu software raid for it to work correctly. Unfortunately, I already partitioned my drives! :( I used the easy way (guided with LVM or whatever) and let it do it for me. Now, RAID1 is very important to me! Is there anyway to repartition the disks to use RAID1, or do I need to wipe my computer and reinstall Ubuntu? :confused:

PS: I was planning on following this to partition as RAID1: [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

Thank you so much for taking time to help a total linux newbie!

---

### Post by YesWeCan on 2011-08-02
Hi there and welcome to linux.
First, the RAID options in your bios should all be disabled. These are only for use with Windows. Linux RAID called mdadm does not need this.

It is possible to transform your existing install to RAID1. In fact, it is possible to do just about anything with linux, but it is a question of how complicated it is. For a newbie I would recommend starting from scratch and letting the alternate installer do all the hard work for you.

This is a guide for doing it the hard way: [http://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-system-incl-grub2-configuration-ubuntu-10.04](http://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-system-incl-grub2-configuration-ubuntu-10.04)
It is more complicated than it needs to be IMO and assumes you want separate RAIDs for each partition rather than one RAID partition and logical partitions on top (using LVM) which is a more flexible way to do it. I havent got a more appropriate guide to hand. But it wont be a simple process.

---

### Post by packerac on 2011-08-02
> **YesWeCan said:**
> Hi there and welcome to linux.
First, the RAID options in your bios should all be disabled. These are only for use with Windows. Linux RAID called mdadm does not need this.

It is possible to transform your existing install to RAID1. In fact, it is possible to do just about anything with linux, but it is a question of how complicated it is. For a newbie I would recommend starting from scratch and letting the alternate installer do all the hard work for you.

This is a guide for doing it the hard way: [http://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-system-incl-grub2-configuration-ubuntu-10.04](http://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-system-incl-grub2-configuration-ubuntu-10.04)
It is more complicated than it needs to be IMO and assumes you want separate RAIDs for each partition rather than one RAID partition and logical partitions on top (using LVM) which is a more flexible way to do it. I havent got a more appropriate guide to hand. But it wont be a simple process.

Well, I guess I haven't done TOO much on my computer yet, so I guess I could start over again. (Though it isn't exactly preferable) If I did decide to re-install Ubuntu server, how would I go about doing it? Last time I did, I wiped both my HDDs before trying to reinstall via CD, because otherwise I kept getting a black screen. And that took FOREVER. If there is a much easier way to go through installation again I might do it.

If I do decide to do it, do I just follow these instructions during installation:
[https://help.ubuntu.com/community/In...n/SoftwareRAID](https://help.ubuntu.com/community/In...n/SoftwareRAID)  ???

Also, when it prompts me on what server software I want to install during installation, should I just choose none of them (like I did before)? Or do I want the SQL thing etc.?

I was told that the BIOS RAID1 setup would work fine... I guess not. :frown:

---

### Post by YesWeCan on 2011-08-02
I can give you instructions to transform your existing installation to RAID1 if you want to have a go at it. Give me some idea how tech-savvy you are. Please post the output of [COLOR=Navy]sudo fdisk -l[/COLOR]

Otherwise, yes that Ubuntu page will give you a basic RAID setup.

The bios RAID is explained here: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
Like I say, you can do just about anything with linux and you can use the linux dmraid drivers to use a fakeraid and coax Ubuntu to install to it. But it is a headache you really don't need when you can do it all using mdadm, which many consider to be better anyway.

---

### Post by packerac on 2011-08-02
> **YesWeCan said:**
> I can give you instructions to transform your existing installation to RAID1 if you want to have a go at it. Give me some idea how tech-savvy you are. Please post the output of [COLOR=Navy]sudo fdisk -l[/COLOR]

Otherwise, yes that Ubuntu page will give you a basic RAID setup.

The bios RAID is explained here: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
Like I say, you can do just about anything with linux and you can use the linux dmraid drivers to use a fakeraid and coax Ubuntu to install to it. But it is a headache you really don't need when you can do it all using mdadm, which many consider to be better anyway.

I consider myself to be decently tech-savvy, but compared to ubuntuforum users probably not so much. I am willing to try my best at whatever you tell me to do though!

This is the output:
> sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f3cfe

   Device Boot      Start         End      Blocks   Id  System

Unable to open -
/dev/sda1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32       60802   488134657    5  Extended
/dev/sda5              32       60802   488134656   8e  Linux LVM

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x41413535

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/dm-0: 491.5 GB, 491488542720 bytes
255 heads, 63 sectors/track, 59753 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-0 doesn't contain a valid partition table

Disk /dev/dm-1: 8308 MB, 8308916224 bytes
255 heads, 63 sectors/track, 1010 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-1 doesn't contain a valid partition table

Disk /dev/dm-2: 8308 MB, 8308916224 bytes
255 heads, 63 sectors/track, 1010 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe32c47f2

Disk /dev/dm-2 doesn't contain a valid partition table

---

### Post by YesWeCan on 2011-08-02
Ok, let's have a go! There are 4 stages, not too complicated:
Stage 1: Create a degraded array on the unused disk
Stage 2: Copy your existing files across
Stage 3: Install the Grub boot-loader
Stage 4: Reboot and rebuild the array (assimilate the original disk into the array)

But first, some housekeeping.
- Disable all RAID options in your bios
- Back up any vital files somewhere safe
- Configure your existing Grub so that it always shows a menu at boot (this will simplify things later). See: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
- Post the output of [COLOR=Navy]sudo blkid[/COLOR]
- Post the output of [COLOR=Navy]cat /etc/fstab[/COLOR]
- Run [COLOR=Navy]sudo dmraid -E -r /dev/sda [/COLOR]and [COLOR=Navy]sudo dmraid -E -r /dev/sdb[/COLOR] to make sure there are no dmraid metadata blocks on your disks

:)

---

