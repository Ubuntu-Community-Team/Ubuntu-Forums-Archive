---
title: "Cannot install to raid0"
date: 2008-05-09
forum: Installation &amp; Upgrades
---

### Post by LordVeovis on 2008-05-09
Ok I am starting to get frustrated now.  I have logged about 35 hours in the past week trying to get my PC up and running again.  Recently I had a crash and need to reinstall.  I have been wanting to install on a raid0 for a LONG time now and have not had any success when I tried in the past.  I decided this time I would tough it out and find out what to do.

I have tried every walkthru, every post, every suggestion that I can find and I still have come no closer this time.

I have tried both Software raid and fakeraid and neither has worked.

Current state: I have installed onto a software raid (not fake raid) and have a separate /boot partition and have it set as bootable, grub SHOULD be installed properly, but when I try to boot the drive it says it is not a bootable drive.  Other errors I have recieved in the past were all sorts of different grub errors, like 17, 14, 15, 21 (not sure 100% if these were them, but I have seen all these recently)

I have tried a total of 6 different istallation walkthrus (both fakeraid and software raid) to no success... Does anyone actually have a succesfully working procedure for installation of a raid0 weather software or fakeraid (pref software as i now have a scsi card - without raid on it - and have 2 15k rpm drives I want to put in raid0

Any help greatly appriciated...

---

### Post by LordVeovis on 2008-05-09
I guess I should also add that with my current "install" I can mount the drives (after I install mdadm) with a live CD and can do any grub changes that may need done...

---

### Post by dstew on 2008-05-09
You can install to a software RAID if you use the Alternate Install CD. It has menu items to set up, partition, and install to software RAID. You can also do it with a network install, like unetbootin. But, the Live CD does not have the ability to create and install to a software RAID, as far as I know.

I used this method to install Feisty to a software RAID. I had 4 120GB disks. I made a small RAID-1 for a /boot partition, and from the rest I made a RAID-5 for the / partition. In order for grub to boot, you need either an un-RAIDed /boot partition, or a /boot partition on a RAID-1 (mirrored). Grub cannot see any software RAID, but the mirrored RAID can be booted by grub because all the data is on each disk. But grub cannot boot striped RAID like RAID-0 or RAID-5.

---

### Post by LordVeovis on 2008-05-09
I do aoppriciate the fast response, I guess I might not have mentioned it above, but I do have a separate /boot, I found out (after my 2nd attempt since almost none of the walkthrus mention this) that it was needed.

Also I know the alternative CD is needed, I merely use the live cd so i can get into a "working" environment to post here.  I can use mdadm from a live cd to monitor, edit, change, etc. the raid, but as u said it isn't able to be installed to from a live cd.  this i knew.

If it helps at all, this sounds strange, but it works... the aformentioned instalation that crashed is still in my pc on a sepatate drive, the kernel and all are fine, just some sys files got corrupted when i tried to update.  I modified the menu.lst and some other stuff and can get the grub and kernel from that instalation to boot my raid, but the /boot partition b4 the raid wont boot it.  This fix I just now managed to find thru repeated attempts to manually configure grub to work.  I would like to boot using the grub that is supposed to be installed on the /boot partition i made as it is a 15k rpm drive and the opther is only 7200 rpm.

Again thanks for the quick reply.  How did you manage to get yours to work?

---

### Post by kdfuller on 2008-05-10
I have installed software raid0 on my computer several times using this method and it has always worked for me. Hope it helps you.

First - boot from the alt. CD.

Let's say you have two 250 GB HDD's.

To start with
On the first hard drive create a 128MB ext2 partition for /boot
Then create a 896MB Partition for swap.

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

---

### Post by LordVeovis on 2008-05-10
> **kdfuller said:**
> 
Mount the 20GB as / and format it with whatever filesystem you want.
Mount the 478 as /home and format it with whatever filesystem you want.

ok, then install as normal, but what about grub? thats where I keep having hte issues, the installer has successfully installed 3 of the 6 times I tried, but it still failed to boot every time.

I have 3 drives atm:
80gb sata
18.2gb 15k rpm scsi
18.2gb 15k rpm scsi

have latest install as:
80gb drive a data storage (its an old ubuntu install atm still that does not work.  8.04)

1st 18.2 drive
   1gb /boot (made it too big)
   1gb swap
   16.2gb raid0
2nd drive
   2gb swap
   16.2gb raid0

Like I said, I can currently cheat to boot, I have it boot off the bootable 80gb corrupted install and have that use the root of /dev/md0 which is the raid... I would like it to launh the kernel from the 15k rpm, I assume it is not because it is using the bootloader off the 80gb drive, so it should be using that kernel from that drive?

---

### Post by kdfuller on 2008-05-10
Are you using the 80 gb as /home or are you not setting up a separate /home partition? Also is your bios boot order set to boot the drive you made the boot partition on first? That could be your problem.

---

### Post by LordVeovis on 2008-05-10
> **kdfuller said:**
> Are you using the 80 gb as /home or are you not setting up a separate /home partition? Also is your bios boot order set to boot the drive you made the boot partition on first? That could be your problem.

No, the 80gb is not set as /home, it isn't even set to auto mount at start, I just had it in there cuz it has my music and my instalation of WoW.  I had planned on coppying over the data I wanted to my partitions and then reformatting that drive, throwing in my 3 sata 320's and raid 5 them, move music and data I want protected there.  That is the end goal.  I just had to do it in steps because I do not want over heat my pc.  Bad cooling atm (well it would be if I had all 6 drives in there.)  I have already coppied over the WoW installation, but will still need to copy over my music b4 I can reformat the drive.  WoW is working, so I do have a fully functioning install of Ubuntu 8.04, just have to load it strangely.

The scsi drive with the /boot partition (/dev/sda1) is set as the boot device.  I manually (via 'F8' option) select my 80gb as the one to boot at the moment, then I use my modified menu.lst to bood the 2 scsi drives (/dev/sda3 and /dev/sdb2) with root=/dev/md0 which works fine.

The /boot partition of the scsi drive (/dev/sda1 - which is not raided) will not let me boot into a working OS.  I think at the moment that it tells me no OS found (I am at work and can't verify) I had done some more modifying of the grub files there to try to get it to load.  I guess if you could tell me how to re-install grub to my scsi /boot (/dev/sda1) drive, that may fix the problem.  I have looked for how to install grub and have not been able to manually install it to the /boot. since as I said above I can get it to boot using the older 80gb drive's bootloader.

I can copy / paste any files u might want to see when I get home.

The way I have tried to install grub has basically been the same every time

```

grub
>device (hd#) /dev/sdX
>root (hd#,#)
>setup (hd#)
>quit

```

---

### Post by kdfuller on 2008-05-10
The only other suggestion I can offer is to reinstall using the method I posted earlier with the 80gb drive unplugged. I think for some reason the install is seeing the grub on the other disk and skipping it on the new install. I always unplug my XP disk when I install and then configure it in the /boot/grub/menu.lst later. I'm sorry I don't have more to offer as I am relatively new to linux myself. Maybe someone with more experience can help you. Good luck.

---

### Post by LordVeovis on 2008-05-11
> **kdfuller said:**
> The only other suggestion I can offer is to reinstall using the method I posted earlier with the 80gb drive unplugged. I think for some reason the install is seeing the grub on the other disk and skipping it on the new install. I always unplug my XP disk when I install and then configure it in the /boot/grub/menu.lst later. I'm sorry I don't have more to offer as I am relatively new to linux myself. Maybe someone with more experience can help you. Good luck.

Thankyou very much tho for what ua did offer :) much appriciated, I will give that a try as I am now seeing page tearing in some of my gfx and some other issues as well.

---

### Post by LordVeovis on 2008-05-12
Fresh install with just the 2 SCSI drives worked, then added other drives as mentioned, works fine, ty.

---

