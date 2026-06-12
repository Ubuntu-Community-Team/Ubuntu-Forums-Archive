---
title: "Computer won't boot"
date: 2012-02-11
forum: Installation &amp; Upgrades
---

### Post by cgreyeyes on 2012-02-11
I'm currently trying to install Ubuntu on my laptop, but when it reaches the installation of the boot loader, it tells me that it encountered an error and that I must pick a different location to install the boot loader (grub). I tried again, but it wouldn't work. I try again, and now "Continue" button would no longer work, and I was forced to exit the installation.

Now, I try to boot my laptop, but it doesn't do anything. It just restarts continuously and now I can't boot onto neither Windows nor Ubuntu on the hard drive. I tried boot-repair, but that didn't work. Here is a URL to the results: [http://paste.ubuntu.com/838307/](http://paste.ubuntu.com/838307/). Any solutions? Thanks for your answers.

---

### Post by darkod on 2012-02-11
Do you by any chance have raid running on the laptop? Laptops usually have only one disk so raid is very rare.

But the results definitely show a raid member disk, plus it reports invalid mbr signature on /dev/sdb (which would be the second disk, again, do you have two disks? ).

---

### Post by cgreyeyes on 2012-02-11
I only have one hard drive, and I don't think I had any RAID configuration on it, but there is a utility pre-installed on it from Intel.

---

### Post by darkod on 2012-02-11
OK, so if you boot into live mode and do:
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb

See if one or the other command ask you if you want to remove the raid meta data. Since you are not running raid, if any meta data somehow ended up on your disk, it should be safe to remove it.

The run:
sudo fdisk -l (small L)

and post the results. Lets see how it shows the disks.

---

### Post by MAFoElffen on 2012-02-11
> **darkod said:**
> Do you by any chance have raid running on the laptop? Laptops usually have only one disk so raid is very rare.

But the results definitely show a raid member disk, plus it reports invalid mbr signature on /dev/sdb (which would be the second disk, again, do you have two disks? ).
@Darko- Just following on this to see how it pans out.  Almost looks more a like a fakeraid gone somewhere. I see raid on two 500.1GB drives and another 1000.2GB (1GB) drive... If that 1TB drive was split, the math works out for those two earlier drives... But it really isn't listed that way is it.

I see NTFS and FAT... Novell(Novell Netware 386), other filesystems... but, offhand, didn't see a Linux partition nor Linux Swap.

I see lots of references to some type of RAID, that I'm really not familiar with as a "type". Just at home, I have 10 RAID Arrays involving 65 drives between 5 servers. Then at work and for customers...  What I see here is new to me. It did catch my eye.

I've torn down and repaired about a thousand laptops in the past year alone. Laptops with 2 HDD's- I came across one and it was 2 SDD's. 3 HDD's- Have never seen nor heard of such an animal... Unless he's using USB Mass Storage Devices?

Now if this is not running a functional RAID, maybe this is remnants of a previous RAID Array (Superblock) that Windows doesn't see without drivers, but Linux does?  Just curious enough to take an interest in this... Now I'll lurk and see where it goes.

EDIT-- ICH/*ISW* Intel Storage Matrix RAID can be handled via dmraid, although it it usually BIOS configured as it is "handled" within certain Intel Chipsets.

---

### Post by cgreyeyes on 2012-02-11
I'm trying to install Ubuntu, but when it reaches the installation of Grub, it tells me that there is an error and that I should either select a different location to install the boot loader, not install the boot loader, or that I completely halt the installation. I currently have unallocated space for Ubuntu and I'm figuring out what to do. What should I do to install Grub?

My laptop is configured as a 1 TB hard drive from 2 500GB hard drives with RAID 0. I also have 3 primary partitions: one for the SYSTEM, one for Windows, and one for HP's repair tools (not recovery disc).

---

### Post by cgreyeyes on 2012-02-11
Okay, I had this resolved with Windows recovery disc repairing the boot loader, so I can boot into Windows. I also ended up wiping out the partition for Ubuntu. Lastly, I found out that I indeed have 2 hard drives in my computer in RAID 0.

Now I need help with the [installation]("http://ubuntuforums.org/showthread.php?p=11681623#post11681623"). Thank you.

---

### Post by darkod on 2012-02-11
> **cgreyeyes said:**
> Okay, I had this resolved with Windows recovery disc repairing the boot loader, so I can boot into Windows. I also ended up wiping out the partition for Ubuntu. Lastly, I found out that I indeed have 2 hard drives in my computer in RAID 0.

Now I need help with the [installation]("http://ubuntuforums.org/showthread.php?p=11681623#post11681623"). Thank you.

Oh man, you need to know better what you have in your box. If you ran those commands to remove the raid it would have broken it, possibly losing your data.

Anyway, the grub install failed because sometimes it fails when using the standard desktop cd to install onto fakeraid. You need to use the alternate install cd to install with raid support. In most cases grub will install fine.

---

### Post by darkod on 2012-02-11
Also replied to yuor other thread. For raid and/or lvm installations, the recommendation is to use the alternate install cd (image). If you do it with the standard desktop cd, grub install sometimes fails, as you noticed.

---

### Post by MAFoElffen on 2012-02-11
> **darkod said:**
> Oh man, you need to know better what you have in your box. If you ran those commands to remove the raid it would have broken it, possibly losing your data.

Anyway, the grub install failed because sometimes it fails when using the standard desktop cd to install onto fakeraid. You need to use the alternate install cd to install with raid support. In most cases grub will install fine.
Another addition to that- Create your linux and swap as Logical partitions. I see the primary partions count as 3, limit is 4 or 3 + Logicals.

---

### Post by cgreyeyes on 2012-02-11
Okay, so I've installed Ubuntu, but grub still refuses to install. The instructions recommend that I set the boot loader to /dev/sda. I use that location, but it won't happen still. I read MAFoElffen's reply in my other post, but I'm not entirely sure what they mean. Meanwhile, the OS is installed in the 4th partition as a primary partition. Now I'll see if I can install grub through the alternate install CD.

---

### Post by drs305 on 2012-02-11
Threads merged. For clarity and to avoid duplication of effort, please do not open more than one thread on the same topic.

---

### Post by YannBuntu on 2012-02-13
Dear all

> **cgreyeyes said:**
> I tried boot-repair, but that didn't work. Here is a URL to the results: [http://paste.ubuntu.com/838307/](http://paste.ubuntu.com/838307/)

Currently, when RAID is detected, Boot-Repair proposes the user to install mdadm or dmraid.
Here cgreyeyes has chosen mdadm, which seemed to be a wrong choice as no array was detected (mdadm --detail --scan output is null), resulting in a null output of os-prober.
In order to avoid users do such mistake, i would like to enhance Boot-Repair so that it automatically detects the correct RAID type (mdadm or dmraid). If you have RAID knowledge, please could you have a look at this: [http://ubuntuforums.org/showthread.php?p=11687121#post11687121](http://ubuntuforums.org/showthread.php?p=11687121#post11687121) Thanks for your help.

---

