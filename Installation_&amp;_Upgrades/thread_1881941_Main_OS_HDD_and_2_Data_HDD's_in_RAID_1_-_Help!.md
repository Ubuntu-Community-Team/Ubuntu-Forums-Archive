---
title: "Main OS HDD and 2 Data HDD's in RAID 1 - Help!"
date: 2011-11-16
forum: Installation &amp; Upgrades
---

### Post by willb1983 on 2011-11-16
Hi all,
 
I have just built a new mini server (only for accessing files via smb) running Ubuntu Desktop 10.04.3 LTS. I have a 160GB hard drive with just the OS on and 2 500GB drives which I want to setup in RAID 1. I've read through countless pages on configuring RAID within Ubuntu using gparted and mdadam but I can't seem to get this working...
 
Could anyone point me in the right direction?
 
Thanks
 
Will

---

### Post by darkod on 2011-11-16
When you say mini server, are you planning to run the server OS or the desktop OS?

The standard desktop cd doesn't not have built-in support for raid. If you want to use the desktop OS you need to download and use the alternate cd image, that has text based installer and built-in raid support. But at the end you end up with the standard desktop OS.

For the server OS of course you need to use the server cd, that also has built-in raid support.

I guess you were trying with the desktop cd. Try again with either the alternate or server cd depending what you want to use, and it should work fine. Setting up raid1 with it is very intuitive.

When you reach the partitioning step, it basically goes like:
1. Create a partition on both 500GB disks. Mark those partitions as linux raid type.
2. Once you have the raid partitions set, go to Configure Software RAID. Configure raid1 array from them.
3. After that you can set a mount point and create ext4 partition on the raid array, or do it later.
4. Set up the root partition and swap on the 160GB as normal.

That should be it, in short.

---

### Post by willb1983 on 2011-11-16
Thanks for the reply. I have installed the desktop version!

I'll download the server edition and see how I get on with that.

Many thanks :)

---

### Post by darkod on 2011-11-16
I'm not sure if you are aware, but like most linux server versions, ubuntu server is only a text mode. It's not complicated to manage, but it can be "weird" for someone who hasn't worked in text mode only before.

---

### Post by willb1983 on 2011-11-17
Ah, I didn't know that. I'm fairly new to Linux! Our main servers run on Debian which I've had some experience with rebuilding the RAID after a failed hard drive. As for Ubuntu Server, I will need the GUI as I run a couple of VM's on there also through VirtualBox.
 
I have found in Disk Utility the option File - Create RAID Array. It's allowing me to select my 2 500GB drives and create either a striped array or a mirror array. Seems to be exactly what I'm looking for!

---

### Post by darkod on 2011-11-17
Well, you can give it a go but I have never tried installing raid that way.

If you want to use raid and the desktop system (not server), that the suggested way of installing is using the alternate install cd, it has support for raid during the install and it still installs the GUI desktop version of ubuntu.

But since you already have an installation give the Disk Utility a go first if you want to.

---

### Post by willb1983 on 2011-11-17
I'll see how I get on and let you know. It was really easy to setup, almost too easy! I'll test a few files and see how it performs in a few minutes.

---

### Post by willb1983 on 2011-11-17
The array is up and running fine apart from on reboot. It won't auto mount on reboot. I configured my fstab as I did previously to mount a second drive on boot. The RAID won't mount and further more won't automatically start on boot. What do I need to edit? A line in the mdadm.conf?

Thanks!

---

