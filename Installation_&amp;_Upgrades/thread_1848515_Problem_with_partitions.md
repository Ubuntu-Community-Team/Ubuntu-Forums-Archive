---
title: "Problem with partitions"
date: 2011-09-22
forum: Installation &amp; Upgrades
---

### Post by ericg27 on 2011-09-22
Alright, so I've been through some threads and a lot loosely relate to my problems and the solutions seem to help but I feel as if I am running around in circles.

I'm a bit of a noob so things will need to be explained to me but here is what I've encountered so far.

I received a computer and I'm not sure what happened to it but what I do know is when I got it, the hard drive's OS had been deleted for whatever reason.  So I decided to try Linux Mint 9 but I came across an error of "the ext4 file system creation in partition #1 (0,0,0)(sda) failed."  I figured maybe it's just the disk so I decided to try Ubuntu and I could not get past the installation set up screen.  I read through some threads and found out it is probably do to a bad partition which I thought maybe explained why mint didn't work either.  So I used GParted and found the problematic partition and went ahead and cleaned the whole drive.  I tried Ubuntu again and it went right past the set up screen and I figured I had solved the problem.... until half way through the installation I get the error "the ext4 file system creation in partition #1 (0,0,0)(sda) failed."  It's the same error that I got with Mint.  

Does anyone know how to solve this problem?

---

### Post by coffeecat on 2011-09-22
Welcome to the forum!

I would look at two possibilities at first. Either the hard drive is failing or, hopefully, it's as simple as a corrupted partition table which is making things difficult.

Boot up the Ubuntu live CD. Open Disk Utility. You don't say which version of Ubuntu. If it's 11.04 with the Unity desktop (launcher on the left), the click on the Ubuntu logo top left and start typing "disk" in the search bar - it will appear in the dash. If classic gnome with the menus in the top panel, you'll find Disk Utility in System > Administration. Highlight your internal drive in the left pane and look for SMART data in the right. Run a self-test. 

If that passes, open Gparted. Assuming you have nothing on that drive you want to keep, go to the Device menu and click on Create partition table. OK that. You will now have a completely unallocated drive with a fresh partition table. See if you can create any partitions.

---

### Post by YesWeCan on 2011-09-22
GParted is not needed. Disk utility will renew the MBR and partition table with its "Format Drive" function.

---

### Post by ericg27 on 2011-09-22
> **coffeecat said:**
> Welcome to the forum!

I would look at two possibilities at first. Either the hard drive is failing or, hopefully, it's as simple as a corrupted partition table which is making things difficult.

Boot up the Ubuntu live CD. Open Disk Utility. You don't say which version of Ubuntu. If it's 11.04 with the Unity desktop (launcher on the left), the click on the Ubuntu logo top left and start typing "disk" in the search bar - it will appear in the dash. If classic gnome with the menus in the top panel, you'll find Disk Utility in System > Administration. Highlight your internal drive in the left pane and look for SMART data in the right. Run a self-test. 

If that passes, open Gparted. Assuming you have nothing on that drive you want to keep, go to the Device menu and click on Create partition table. OK that. You will now have a completely unallocated drive with a fresh partition table. See if you can create any partitions.

Sorry, I have 11.04, I am under Disk Utility however I don't see self test. I see "Smart Status: Not Supported".  I tried formatting the drive with the built in tool under Disk Utility and it gave me an error.  

The details are > Error creating partition table: helper exited with exit code 1: In part_create_partition_table: device_file=/dev/sda, scheme=0
got it
got disk
committed to disk
BLKRRPART ioctl failed for /dev/sda:
Device or resource busy

---

### Post by coffeecat on 2011-09-22
The self-test is part of SMART, so if the disk doesn't support SMART then you won't be able to do a self-test, unfortunately. It's a bit unusual for a HD made in the last few years not to support SMART. Do you know how old the machine is?

SMART, by the way, is the self-monitoring of a hard drive. More here:

[http://en.wikipedia.org/wiki/S.M.A.R.T](http://en.wikipedia.org/wiki/S.M.A.R.T).

To your partition table. The "Device or resource busy" suggests that a partition has been mounted, that is if the installer managed to create any partitions at all. Open Gparted, yes you do need Gparted this time. Are there any partitions? If so, is there a lock icon by them? If there's a swap partition with a lock, right-click and "swapoff". If another type of partition, right-click and "unmount". Now try to create a partition table with Gparted.

If that doesn't work, the only other suggestion I have is to zero the area of the disk with the partition table. I can tell you how to do that, but probably not until tomorrow. I have to log off soon.

---

### Post by ericg27 on 2011-09-22
It's a gateway laptop that is 2-4 years old. I'm not sure, all I know is it was originally booted with Vista from the sticker on it.

I loaded GParted and only one partition shows up and it's unallocated and taking up the entire drive.

---

### Post by YesWeCan on 2011-09-22
One partition? Would you post the output of
sudo sfdisk -luS

---

### Post by coffeecat on 2011-09-22
OK, you've just caught me before I log off in a few minutes. :)

Actually - point of information - when I said you did need Gparted in my previous post, you could in fact have used Disk Utility, but if there had been viable partitions, it would have been easier to see what's what in Gparted. Unallocated taking up the whole drive means there is no partition, by the way.

How to zero the partition table. Open a terminal, and:

```
sudo dd if=/dev/zero of=/dev/sda bs=512 count=1
```

Double-check what you type. The operation will take moments only. Now see if you can create a partition table with Gparted.

---

### Post by ericg27 on 2011-09-22
Well I don't think it is an actual partition, the whole drive is labeled as unallocated. That would mean there are no partitions, correct?

---

### Post by Blasphemist on 2011-09-22
If it makes more sense for you, under the view menu in GParted, choose device information. See my screen shot for an example.

---

### Post by YesWeCan on 2011-09-22
You should not have GParted running at the same time as you try to format in Disk Utility, BTW. That may explain the device busy error.

Let's see sudo sfdisk -luS

---

### Post by ericg27 on 2011-09-22
> **coffeecat said:**
> OK, you've just caught me before I log off in a few minutes. :)

Actually - point of information - when I said you did need Gparted in my previous post, you could in fact have used Disk Utility, but if there had been viable partitions, it would have been easier to see what's what in Gparted. Unallocated taking up the whole drive means there is no partition, by the way.

How to zero the partition table. Open a terminal, and:

```
sudo dd if=/dev/zero of=/dev/sda bs=512 count=1
```Double-check what you type. The operation will take moments only. Now see if you can create a partition table with Gparted.
So once I do that it should be good to try and instal again?

@ yeswecan, I don't have both running at the same time. I am using two separate disks for them.

---

### Post by coffeecat on 2011-09-22
> **ericg27 said:**
> So once I do that it should be good to try and instal again?

Once you do that dd command, there will be no partition table at all. Which is why you need to use Gparted to try to create a partition table after doing it. I think the installer may do that for you if presented with a drive with no partition table, but it doesn't hurt to create one first. If the create partition table fails in Gparted after you have zeroed that area of the drive, then I fear you *may* have a failing drive, which is why I was hoping that SMART data might help. But see what others say as well.

---

### Post by coffeecat on 2011-09-22
> **ericg27 said:**
> 
@ yeswecan, I don't have both running at the same time. I am using two separate disks for them.

Ah. As YesWeCan says, don't try to use both Disk Utility and Gparted at the same time - that could be the cause of the problem. Close Disk Utility and use Gparted. Don't do the dd command yet. See if Gparted can create a new partition table with Disk Utility closed.

---

### Post by YesWeCan on 2011-09-22
The dd MBR erase might work but I suspect there is something more sinister going on here. Maybe a disk sector fault somewhere. It is really odd that the installer could not format a partition.

Make absolutely sure your drive is called sda if you have more than one drive. From earlier posts I think not but if anyone else is reading this it is essential to run sfdisk or fdisk to check the drive letter before running the dd command. After running the dd command you need to tell the kernel to re-read the partition table or it won't notice:
[COLOR="DarkSlateBlue"]sudo hdparm -z /dev/sda[/COLOR]

---

### Post by ericg27 on 2011-09-22
> **coffeecat said:**
> Ah. As YesWeCan says, don't try to use both Disk Utility and Gparted at the same time - that could be the cause of the problem. Close Disk Utility and use Gparted. Don't do the dd command yet. See if Gparted can create a new partition table with Disk Utility closed.
Well no that is what I am saying. GParted is on it's own disk, I don't even have Ubuntu running while I'm using GParted.

Anyway, so I clicked device> create partition table.  What needs to be done now? Do I create a partition? and if so how big?

> **YesWeCan said:**
> The dd MBR erase might work but I suspect there  is something more sinister going on here. Maybe a disk sector fault  somewhere. It is really odd that the installer could not format a  partition.

Make absolutely sure your drive is called sda if you have more than one  drive. From earlier posts I think not but if anyone else is reading this  it is essential to run sfdisk or fdisk to check the drive letter before  running the dd command. After running the dd command you need to tell  the kernel to re-read the partition table or it won't notice:
[COLOR=DarkSlateBlue]sudo hdparm -z /dev/sda[/COLOR]
I'm positive the drive is sda.

---

### Post by coffeecat on 2011-09-22
> **ericg27 said:**
> Well no that is what I am saying. GParted is on it's own disk, I don't even have Ubuntu running while I'm using GParted.

I think we're getting confused between hard disks and optical disks here. As far as I can see you have just one hard drive, sda, because you are using a laptop. Do you mean you are using the Gparted live CD? I was assuming you were using Gparted from the Ubuntu live CD, which means that you would be running Gparted in an Ubuntu live session.

> Anyway, so I clicked device> create partition table.  What needs to be done now? Do I create a partition? and if so how big?

Did you get an error after create partition table? If not, then it may have worked, and you could try the installer.

---

### Post by ericg27 on 2011-09-22
> **coffeecat said:**
> I think we're getting confused between hard disks and optical disks here. As far as I can see you have just one hard drive, sda, because you are using a laptop. Do you mean you are using the Gparted live CD? I was assuming you were using Gparted from the Ubuntu live CD, which means that you would be running Gparted in an Ubuntu live session.



Did you get an error after create partition table? If not, then it may have worked, and you could try the installer.
Yeah I meant I was loaded off a DVD.

and I didn't get an error so I guess it worked. I'll try to install Ubuntu again.

---

### Post by ericg27 on 2011-09-22
ok, so I started install before I had to run out and do some stuff and when I came back it read
Read-error on swap-device [some number:some other number]
 Read-error on swap-device [some number:some other number]
all the way down the page. 

I rebooted from the disk and SMART data started working again and it  says "554 bad sectors, disk failure is imminent" So I guess that is my  problem.

---

### Post by coffeecat on 2011-09-23
> **ericg27 said:**
> I rebooted from the disk and SMART data started working again and it  says "554 bad sectors, disk failure is imminent" So I guess that is my  problem.

I'm sorry to hear that. It does explain the difficulties you encountered.

---

