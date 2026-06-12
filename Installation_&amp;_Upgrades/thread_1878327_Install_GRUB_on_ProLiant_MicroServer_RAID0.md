---
title: "Install GRUB on ProLiant MicroServer RAID0"
date: 2011-11-09
forum: Installation &amp; Upgrades
---

### Post by Kimm3 on 2011-11-09
Hi,
I'm currently playing around with my new Hp Proliant Microserver, trying to install Ubuntu server 11.10... I'm definitly not an expert on any of this, just a beginner.
 
What I've done is I've created a RAID0 with the "built-in" RAID controller. Then I went on installing ubuntu. When I came to the installation of the GRUB bootloader, it asks what harddrive/device I want to install it on. The "suggestion" is set to /dev/mapper... And this is where I don't know what to do. When I press continue an error appears because it can't find the device, I've tried /dev/sda and a couple of others, same error. I went through the partition part without troubles, choosing "Use entire disk and LVM" or something similiar.
 
How do I know what the device name is!?
 
Would really appreciate your help on this.
 
Thanks!
 
PS. 64-bit version of Ubuntu server 11.10

---

### Post by pauldmallett on 2011-12-10
Hi, Sorry I do not have an answer for you but I am very interrested to learn if this installation is possible as like you I am fairly new to Linux but also wish to load Ubuntu on HP ProLiant N40L 1P Micro Server and set up RAID-0.
Please post if you sort this out so I can go ahead and buy one, thanks in advance.

---

### Post by darkod on 2011-12-10
I believe you have to have a separate /boot partition outside of the LVM. I don't know if the auto LVM process does this.

Since this is a new install with no important data, try this:
1. Go into the RAID setup and remove the current raid0 array.
2. Create a small raid1 array of 500MB for example.
3. Create the main raid0 from the rest of the space.
4. During install I suggest to use the Manual option, not the automatic ones. It's quite easy to use.
5. Create a ext4 partition on the raid1 device, mount point /boot.
6. Create LVM device on the raid0 device.
7. Go in Configure LVM option above the partitions list. That will start the LVM set up.

Try to install grub2 to the /dev/mapper, I believe it's better to be there.

See if that worked.

Another option is to use the ubuntu software raid instead of the mobo raid.

PS. Are you aware of the danger of running raid0 for your data? If one disk fails you lose all the data. Raid0 is not a proper redundancy raid.

---

### Post by pauldmallett on 2011-12-10
Thanks for that; sorry I am a little rusty on small server building (I have only put a couple together using Windows but I have been waiting for the chance to use Ubuntu and that chance has now arrived), I should have specified RAID 1 or 1+0 for data security. The issue here seems to be the recognition of the onboard RAID controller however Linux software RAID seems a popular choice. I will see what more I can discover over the week end. Thanks again.

---

### Post by darkod on 2011-12-10
I actually bought the Proliant Microserver with N36L like a week ago, but the version with only single SATA disk so I'm not running any raid. At least until the floods in Thailand allow the HDD manufacturing to pick up again and the prices to drop. Planning to run software RAID1 but I have no intention paying 1TB around 150€.

---

