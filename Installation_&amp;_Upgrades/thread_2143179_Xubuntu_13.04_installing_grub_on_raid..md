---
title: "Xubuntu 13.04 installing grub on raid."
date: 2013-05-08
forum: Installation &amp; Upgrades
---

### Post by gravysteak on 2013-05-08
Like the last version of ubuntu 13.04 fails to install grub on my raid array.
So no problem if I can remember correctly what I did last time (after some googling).

I tried to install and setup grub from livecd like this.

```
sudo mount /dev/mapper/isw_beabccfhaa_Volume0p1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/mapper/isw_beabccfhaa_Volume0

sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt
sudo update-grub
```

Which gives me these errors.
```
sudo: unable to resolve host xubuntu
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found initrd image: /boot/initrd.img-3.8.0-19-generic
Found memtest86+ image: /boot/memtest86+.bin
ERROR: ddf1: seeking device "/dev/dm-2" to 18446744073709421056
ERROR: hpt37x: seeking device "/dev/dm-2" to 4608
ERROR: hpt45x: seeking device "/dev/dm-2" to 18446744073709547008
ERROR: isw: seeking device "/dev/dm-2" to 18446744073708469760
ERROR: sil: seeking device "/dev/dm-2" to 18446744073709289984
done
```

Upon trying to boot it just sits on the loading screen.

Just had a look at the boot up. It throws up those same errors and then sits on Starting cups-browsed

Any help would be greatly appreciated.

---

### Post by darkod on 2013-05-08
Did you use LVM too? Quick google search shows /dev/dm-N devices mentioned as LVM devices. I'll keep on reading.

Otherwise, the fakeraid grub2 install should be like you tried. Under the assumption that p1 is your root partition. Are you sure about that?

---

### Post by gravysteak on 2013-05-08
Yeah I double checked p1 is root. I just did a standard install on my intel raid controller and let the installer handle partitioning automatically, so I guess I'm not using LVM.

---

### Post by darkod on 2013-05-09
This seems to a bug then. Just to remind you, the automatic options also support LVM if you select it, but if you did I guess you would know about it. It looks like grub-probe is getting confused whether there is LVM or not, because according to google the dm-2 devices refer to LVM.

So right now, does it boot ubuntu at all or not? I see grub-update detects the kernel, but I'm not sure if it boots.

---

### Post by gravysteak on 2013-05-09
It starts loading daemons but stops after cupsbrowsed

---

### Post by darkod on 2013-05-09
Hm, not sure if they are related or not. Is there a cups error log like /var/log/cups/error_log? It might have more details.

The thing is, I am starting to doubt if the update-grub errors have anything to do with it not booting. Surely they shouldn't be there, but since it finds the kernel correctly it should try to boot (maybe?). On the other hand, the cups error might not be related to this raid error at all, I don't see how cups would be related to raid. This cups error might be the one actually stopping you to boot.

---

### Post by gravysteak on 2013-05-09
Heres the error in cups log.

```
E [10/May/2013:08:58:19 +1000] Unable to bind socket for address [v1.::1]:631 - Cannot assign requested address.
```

And heres my boot log.

```
ERROR: ddf1: seeking device "/dev/dm-2" to 18446744073709421056
ERROR: hpt37x: seeking device "/dev/dm-2" to 4608
ERROR: hpt45x: seeking device "/dev/dm-2" to 18446744073709547008
ERROR: isw: seeking device "/dev/dm-2" to 18446744073708469760
ERROR: sil: seeking device "/dev/dm-2" to 18446744073709289984
fsck from util-linux 2.20.1
/dev/mapper/isw_beabccfhaa_Volume0p1: clean, 145826/60923904 files, 4465979/243667904 blocks
 * Starting bluetooth daemon[164G[ OK ]
 * Starting mDNS/DNS-SD daemon[164G[ OK ]
 * Starting CUPS printing spooler/server[164G[ OK ]
 * Starting cups-browsed - Bonjour remote printer browsing daemon[164G[ OK ]
 * Starting emergency keypress handling[164G[ OK ]
 * Stopping Bridge file events into upstart[164G[ OK ]
 * Stopping device node and kernel event manager[164G[ OK ]
 * Stopping system logging daemon[164G[ OK ]
 * Stopping cups-browsed - Bonjour remote printer browsing daemon[164G[ OK ]
 * Stopping Initialize or finalize resolvconf[164G[ OK ]
 * Stopping emergency keypress handling[164G[ OK ]
 * Starting System V runlevel compatibility[164G[ OK ]
 * Starting save system clock to hardware clock[164G[ OK ]
 * Starting store software rfkill state[164G[ OK ]
 * Starting save sound card(s') mixer state(s)[164G[ OK ]
 * Stopping Bridge udev events into upstart[164G[ OK ]
 * Stopping store software rfkill state[164G[ OK ]

Warning: Fake initctl called, doing nothing.
 * Starting save sound card(s') mixer state(s)[164G[[31mfail[39;49m]
 * Stopping CUPS printing spooler/server[164G[ OK ]

```

---

### Post by darkod on 2013-05-09
In an older thread, reinstalling upstart worked to solve a similar error. Not sure about your case but it doesn't hurt trying. Since you can't boot you will have to do it from chroot.

Do the chroot procedure you posted in your post #1, only the mount commands and the chroot commands (you don't need the grub-install for this).

Once you are inside the chroot note that you are already as root, so you don't need sudo in front of any command. Try:
```
apt-get install --reinstall upstart
```

After that exit the chroot with 'exit' unmount all and reboot. I don't think it will help but it's worth the try. :)

---

### Post by darkod on 2013-05-09
Listen, just to test something, can you also boot into live mode and post the output of this:
```
sudo apt-get install lvm2
sudo dmraid -ay
sudo vgchange -ay
sudo parted -l
```

Lets see what it displays.

---

### Post by gravysteak on 2013-05-09
```
xubuntu@xubuntu:~$ sudo dmraid -ay
ERROR: ddf1: seeking device "/dev/dm-2" to 18446744073709421056
ERROR: hpt37x: seeking device "/dev/dm-2" to 4608
ERROR: hpt45x: seeking device "/dev/dm-2" to 18446744073709547008
ERROR: isw: seeking device "/dev/dm-2" to 18446744073708469760
ERROR: sil: seeking device "/dev/dm-2" to 18446744073709289984
RAID set "isw_beabccfhaa_Volume0" already active
RAID set "isw_beabccfhaa_Volume0p1" already active
RAID set "isw_beabccfhaa_Volume0p5" already active
xubuntu@xubuntu:~$ sudo vgchange -ay
  No volume groups found
xubuntu@xubuntu:~$ sudo parted -l
Error: Can't have a partition outside the disk!                           

Model: ATA WDC WD5000AAKX-0 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  500GB  500GB  primary  fat32        boot, lba


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/isw_beabccfhaa_Volume0p5: 2146MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  2146MB  2146MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/isw_beabccfhaa_Volume0p1: 998GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  998GB  998GB  ext4


Error: Can't have a partition outside the disk!                           

Model: Linux device-mapper (striped) (dm)
Disk /dev/mapper/isw_beabccfhaa_Volume0: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End     Size    Type      File system     Flags
 1      262kB  998GB   998GB   primary   ext4
 2      998GB  1000GB  2146MB  extended
 5      998GB  1000GB  2146MB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!
```

---

### Post by gravysteak on 2013-05-09
apt-get isn't playing
```
root@xubuntu:/# apt-get install --reinstall upstart
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of upstart is not possible, it cannot be downloaded.
```

upon apt-get update i get i bunch of errors like this
```
root@xubuntu:/# apt-get update
Err http://au.archive.ubuntu.com raring Release.gpg                            
  Something wicked happened resolving 'au.archive.ubuntu.com:http' (-11 - System error)

```

---

### Post by darkod on 2013-05-09
Hold on, how many disks do you have? Is this two 500GB disks in one 1TB raid0 array?

Look at the parted results:
1. First immediately it complains that /dev/sda has a partition outside the disk. Because of this it doesn't display any partitions on sda.
2. Then it says /dev/sdb has a single fat32 partition on the whole disk. This can't be true if the disk is part of raid0 array with linux partitions on it. Why would it say it can see fat32 partition there?
3. Then it says p1 is out of the disk (the root partition), but that error might not mean much since often it can't see inside the fakeraid correctly, so it might be wrongly reported error.

This looks like big chaos in the partitioning. If you are running only ubuntu, any chance to move to mdadm software raid? You only need the fakeraid for dual boots, otherwise mdadm is much better solution, and you will have less issues with it while still having better flexibility.

---

### Post by gravysteak on 2013-05-09
Yeah 2 500gb in raid 0.
I have no idea why its saying there is a fat32 partition got me beat.
I dual boot windows 7. All my other drives are unpluged at the moment.

---

### Post by darkod on 2013-05-09
Is win7 on this array too? It doesn't show it in the array, it only shows ext4 root partition and the swap partition, as you can see.

Or win7 is on another disk that is disconnected right now?

---

### Post by gravysteak on 2013-05-09
Yeah its on a dissconnected drive.

---

### Post by Slim Odds on 2013-05-09
As far as I know, there is no way to have /boot on a RAID0 partition. The /boot directory contains the kernel and has to available before the RAID drivers can be loaded. On my system in the past, I had a separate partition for /boot and then a RAID0 partition for /

---

### Post by gravysteak on 2013-05-09
It worked this way before.

---

### Post by darkod on 2013-05-09
That's true for software raid, fakeraid should still work without /boot outside the array. Maybe it doesn't any more. :)

Anyway, when I said you can't use SW raid for dual boot I was assuming both OSs on the same disks/array. Since you have win7 on another disk, there is nothing stopping you using mdadm. When I saw you have only ubuntu on the /dev/mapper/... device that says it all. Windows won't be able to "look into" the raid but it can't open linux partitions anyway. Not without using additional programs/drivers that I personally don't trust.

We have come to a point where I have no idea what to do next. Plus the setup/info on this disks is really weird, like the underlaying fat32 partition it seems to report. It almost looks like the array was created and the process didn't delete the underlaying partitions, which it should do because when you create the array it should destoy all data. Hwoever since fakeraid is not real raid, who knows how it did it. :)

If you want to go ahead with the mdadm option, we can provide help. In that case you will need /boot outside the raid0, for example raid1 of two small 1GB partitions at the start of the disks for /boot. Then raid0 of the big partitions for /. Swap you don't neep to put in a raid, you can have two identical partitions on both disks and use them both like that. Which ever you want.

If you need to take data out, live mode should be able to read the p1 since it mounted it correctly when you were doing the initial grub-install attempt. Or maybe not? if you need to copy the data, look if you can open and read the partition from live mode.

I don't know what else to suggest, sorry. Mdadm is definitely better option if you don't need windows on the same array. Let me know if you want to go ahead, because there are few things to do before you start installing your new ubuntu with mdadm.

---

### Post by Slim Odds on 2013-05-09
Those are good points Darkod, I never bothered with fakeraid. I've always use mdadm, which works great once you get it set up properly.

---

### Post by gravysteak on 2013-05-10
I just tried to install 12.10 back on the errors aren't there and its still hanging at boot. Do you think maybe there is something else going on?

I will try an install without raid. I don't want to go through the trouble of setting up mdadm if theres something else wrong with my system.

By the way thanks for all the help guys.

---

### Post by gravysteak on 2013-05-10
OK it works fine without raid. I'm scratching my head as to how I had 12.10 working but anyway.

How hard is it to setup mdadm? I think i'll take that route.

---

### Post by darkod on 2013-05-10
It's very easy. I would say the planning part is most difficult, and important at the same time. The only thing to watch out with mdadm is that each partition you want, is a separate md device (array). It's not like with fakeraid or HW raid where you have the array and you partition it further.
There is no partitioning a md device.

So you need to plan how many partitions you want, their sizes, and make the partitions on the disk and the md devices accordingly.

Since you want to use raid0, as minimum you need separate /boot partition which means separate raid1 md device.

Lets assume you want a single root partition for the system. I prefer partitioning in parted on the command line since it gives best control and selection of units you want to use.

Lets assujme the disks are /dev/sda and /dev/sdb. Be careful when partitioning if you have more disks to select the correct ones. To have a 1GB /boot partition and a total of 4GB swap for example, do this in live mode in terminal:
```
sudo parted /dev/sda
unit MiB
print #(write down the total number of MiB the disk has)
mklabel msdos #(new blank msdos partition table)
mkpart primary 1 1025 #(make partition starting at 1 ending at 1025 MiB, which means 1024MiB = 1 GiB)
set 1 raid on #(set raid flag on the partition so you know it's for raid)
mkpart primary 1025 TOT-5000 #(make one big primary partition from 1025 to total number of MiB minus 5000 for swap at the end)
set 2 raid on
mkpart logical TOT-4999 TOT-3
quit
```

That should create 1GB primary partition at start (sda1), 4GB logical partition at end (sda3), and big primary partition between them (sda2).

Do the same for /dev/sdb.

After that you have the disks identical, you need to add mdadm and create the two devices for /bot and /.
```
sudo apt-get install mdadm
sudo mdadm --create --verbose --level=1 --raid-devices=2 /dev/md0 /dev/sda1 /dev/sdb1
sudo mdadm --create --verbose --level=0 --raid-devices=2 /dev/md1 /dev/sda2 /dev/sdb2
```

That will create md0 raid1 device and md1 raid0 device.

Format them:
```
sudo mkfs.ext4 /dev/md0
sudo mkfs.ext4 /dev/md1
```

After that click the Install Ubuntu icon, select Something Else (manual install), select /dev/md0, the Change button below, Use As ext4, mount point /boot. For /dev/md1 Use As ext4, mount point /. For both swap partitions, Use As swap area.
Device for bootloader /dev/sda.

That should be it.

If you want a separate /home too, the partitioning layout needs to be different before creating the arrays.

---

### Post by gravysteak on 2013-05-10
Thanks for explaining that. I seem to be able to create the raid arrays ok and start the install but it fails at installing grub onto sda.

I tried to install grub manually but get grub rescue.

I have a question. How will grub be able to see the boot partition if it's in raid? Should I not just create a normal partition for boot on sda instead?

---

### Post by Slim Odds on 2013-05-10
> **gravysteak said:**
> Thanks for explaining that. I seem to be able to create the raid arrays ok and start the install but it fails at installing grub onto sda.

I tried to install grub manually but get grub rescue.

I have a question. How will grub be able to see the boot partition if it's in raid? Should I not just create a normal partition for boot on sda instead?
/boot should NOT be on a RAID array. The mdadm module will not be ready at kernel load time.
Create a separate normal partition for /boot

---

### Post by darkod on 2013-05-10
It's OK if it's on raid1. It can't be on raid0 because the files are split on raid0, while on raid1 they are mirrored. I don't know all the technical details, but if you think it can't be on raid at all, ask yourself this: if you have /boot as a partition on one disk of a mirrored array, and that disk fails, your system will fail too. What kind of raid1 is that???

Of course it can be on raid because that's the point of raid, to have /boot also mirrored so it can boot with one disk failed.

What could be the problem is the fakeraid meta data that I completely forgot about. Remember I mentioned we need to do something first before continuing with mdadm.

Did you go into bios and changed sata mode from raid to ahci?
Boot in live mode and remove the meta data on both disks:
```
sudo dmraid -Er /dev/sda
sudo dmraid -Er /dev/sdb
```

That could fail grub2 since the live cd can't install grub2 on fakeraid successfully and it might be seeing the fakeraid meta data still. Give it a go.

---

### Post by gravysteak on 2013-05-10
Too late I already did it the other way. What you're saying makes sense though. That would be silly for a Raid1 array.

Also thought I'd mention a problem I had before. The installer doesn't install mdadm so I installed it with live cd like this.
```
sudo mount /dev/md0 /mnt
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt
mount /dev/sda1 /boot
apt-get update
apt-get install mdadm
```

pheww!! now it boots fine.

---

### Post by darkod on 2013-05-10
In your case a raid1 /boot wouldn't help much since your root is raid0 so if one disk dies all is gone anyway. But the statement that it shouldn't be on a raid makes no sense and isn't true. It can't be on raid0, that is correct.

Since I usually install raid with the alternate cd (which doesn't seem to exist for the latest releases), I wasn't sure if the live cd installer installs mdadm in your system or not.

Did you reboot few times? You might also need to update the initramfs or insert the array definition in mdadm.conf.

---

### Post by gravysteak on 2013-05-12
Nope worked first go. Thanks again.

---

