---
title: "Boot Loader failed to install"
date: 2012-06-06
forum: Installation &amp; Upgrades
---

### Post by Messyhair42 on 2012-06-06
I installed ubuntu 12.04 and after detecting my other operating systems GRUB failed to install. I was using the alternate installation disk to install a RAID1 as outlined [here]("https://help.ubuntu.com/10.04/serverguide/advanced-installation.html") Thinking I could use the disk to detect other operating systems I installed it again onto a flash drive but the new OS didn't come up. So I'm without a way to boot into what should be my primary installation and I've never had to deal with something like this before. Help is appreciated.

---

### Post by darkod on 2012-06-06
You can always try to add grub2 from live mode. Did it give any specific error why grub2 didn't manage to install the first time?

From live mode you should be able to access software raid as long as you install the mdadm package and assemble the array (NOTE: ASSEMBLE, not CREATE!!!).

```
sudo apt-get install mdadm
sudo mdadm --assemble --scan
```

That should scan and assemble the array, so you should have the mdX device and the root partition available.

You should be able to install grub2 by mounting the root partition at /mnt and then installing grub2 with something like:
```
sudo mount /dev/mdX /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Since running a raid you might want to run the last command again to install on /dev/sdb too, it's usually best to have the grub2 on both disks in raid.

One possible issue could have been if running gpt partition tables on the disks, because in that case grub2 needs the bios_grub partition and it can fail without it.

---

### Post by Messyhair42 on 2012-06-07
> **darkod said:**
> You can always try to add grub2 from live mode. Did it give any specific error why grub2 didn't manage to install the first time?

From live mode you should be able to access software raid as long as you install the mdadm package and assemble the array (NOTE: ASSEMBLE, not CREATE!!!).

```
sudo apt-get install mdadm
sudo mdadm --assemble --scan
```

That should scan and assemble the array, so you should have the mdX device and the root partition available.

You should be able to install grub2 by mounting the root partition at /mnt and then installing grub2 with something like:
```
sudo mount /dev/mdX /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Since running a raid you might want to run the last command again to install on /dev/sdb too, it's usually best to have the grub2 on both disks in raid.

One possible issue could have been if running gpt partition tables on the disks, because in that case grub2 needs the bios_grub partition and it can fail without it.

If I try this method which console's terminal am I using? I can't see the RAID drive from my thumb drive installation. Is there a terminal if I boot to the installation disk again? I've never tried something like this so I'm a little confused.

---

### Post by darkod on 2012-06-07
Boot with your thumb drive in live mode, Try Ubuntu. Open terminal. And you do everything there. At first it will not see the array because the mdadm package is not included on the live cd (usb) by default.

But after you install mdadm and assemble the array with the first block of commands I gave you, you should see the array.

The second block of commands, especially the first command about mounting root, will depend on how you have your setup. For example, the root partition can be a whole /dev/mdX device, or it can be only a partition on it, in which case it might be like /dev/mdXpY.

On second thought, those command might not work fully, but it's the first thing to try. If grub2 was never installed completely, you might need to enter your installation with chroot and remove it and reinstall it again. I am talking about grub2 only, not the whole ubuntu. But lets take it one step at a time.

First learn to access your array from live mode, it's also useful if you need to access it in emergency in the future. Then try those two commands to reinstall grub2 to the MBR, and then we'll see.

---

### Post by koenr on 2012-06-07
I have more or less the same problem using the information I found on [https://help.ubuntu.com/12.04/serverguide/advanced-installation.html](https://help.ubuntu.com/12.04/serverguide/advanced-installation.html)

I can't do step 8: set the bootable flag. Nothing happens if I click on it (screen flicker and it stays on off). Following step 5 (set physical volume for RAID) seems to make it impossible to set the bootable flag. 

After ignoring the previous, the grub loader fails to install on the master boot record.

I'm still confused about where the booting exactly starts: is it on the first partition of the first disk, or on the first partition of the raid volume?

---

### Post by darkod on 2012-06-07
> **koenr said:**
> I have more or less the same problem using the information I found on [https://help.ubuntu.com/12.04/serverguide/advanced-installation.html](https://help.ubuntu.com/12.04/serverguide/advanced-installation.html)

I can't do step 8: set the bootable flag. Nothing happens if I click on it (screen flicker and it stays on off). Following step 5 (set physical volume for RAID) seems to make it impossible to set the bootable flag. 

After ignoring the previous, the grub loader fails to install on the master boot record.

I'm still confused about where the booting exactly starts: is it on the first partition of the first disk, or on the first partition of the raid volume?

With software raid the boot starts at the MBR (Master Boot Record) of the disk set as first choice to boot in your BIOS. During boot the OS assembles the array.

You don't need the boot flag for linux, it doesn't use it. Sometimes some boards don't boot if they can't detect the boot flag on any partition, I guess that's why the tutorial says to set it. Otherwise, it's not used.

For software raid you should try to install the bootloader to /dev/sda, /dev/sdb, /dev/sdc, etc. Having a boot flag or not should not affect the installation of the bootloader.

As mentioned above, you can try assembling your array in live mode, mounting the root partition and check if core.img exists or not. In should be in /boot/grub folder in your mounted root.
So, for example if the root is mounted at /mnt, you should look for /mnt/boot/grub/core.img. If it's there that's usually a sign grub2 was installed inside the OS, so you can try only reinstalling it to the MBR of the disks. Otherwise, you would need to enter the installation with chroot and reinstall all of grub2 again.

---

### Post by koenr on 2012-06-08
Thanks a lot for this background information - I was surprised to learn that the boot flag is not important in Linux.
I'm restarting the installation from scratch with the extra info in mind. It might be that not booting is a bios problem. It's a Supermicro server board and the boot loader has a lot of options. It shows eg an ubuntu entry to boot from (which doesn't work)
I'll post back if I found a solution.

---

### Post by koenr on 2012-06-08
Aarch, I made a mistake in step 2 and 3:
2. Select the first hard drive, and agree to "Create a new empty partition table on this device?". 
3. Select the "FREE SPACE" on the first drive then select "Create a new partition". 

I combined those 2 steps: I selected the free space on the first hard drive in stead of selecting the drive. You don't get the option of creating a primary or logical partition and can't set later in the process the boot flag, but all the rest works like in the receipe. 
Except you can't install a boot loader later in the process and the system doesn't work :-(

Working system in 20 minutes :-). Thanks again for your help.

---

### Post by Messyhair42 on 2012-06-08
@Darko

I get the mdadm package installed and i can see the filesystem. Because of my first time working with RAID I only have a swap partition and a / partition. the devices making up the RAID are dev/sdc/ and dev/sdd. The array makes up /md1. for the next set of commands I'm using will be ```
sudo mount dev/md1 /mnt

sudo grub-install --root-directory=/mnt /dev/sdc
```

and again with the last command replacing /sdc with /sdd, correct?

I'll probably be away until Sunday when i can dedicate time to working on this.

---

### Post by darkod on 2012-06-08
Yes, if the root is /dev/md1, that's what you would use.

---

### Post by Messyhair42 on 2012-06-10
I just thought of something. I'm running from a usb stick installation of 10.04, which I believe has GRUB 1.98. if I run the grub install command which version will I be installing? Also with the new versions there is no longer a /boot/grub.lst file, how do I configure the grub list for multiple OS?

---

### Post by darkod on 2012-06-10
Grub2 (officially 1.9X) configures itself to detect all OSs and make correct entries for the boot menu. So you shouldn't need to do anything. If you ever add/remove an OS you can update it with:
sudo update-grub

As for reinstalling, you should use live mode of the same version as the system you are repairing. That's the recommendation, not sure if it will work if you ignore it.

---

### Post by Messyhair42 on 2012-06-10
Does the alternate CD have live mode b/c I dont think it does? would a usb installation of 12.04 work the same? I'm on limited bandwidth internet and nearly reached the monthly cap so if I can avoid another 700MB download I will.

---

### Post by darkod on 2012-06-10
The alternate doesn't have live mode. Not sure if you can boot it in some rescue mode though, I rarely use the alternate. Give it a shot.

---

### Post by Messyhair42 on 2012-06-11
```
jason@jason-mobile:~$ sudo grub-install --root-directory=/mnt /dev/sdc
/usr/sbin/grub-probe: error: no mapping exists for `md1'.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

```

After setting up a bootable USB failed I went ahead and tried it from my current 10.04 OS, this is the result of the last code. what does --modules mean?

---

### Post by darkod on 2012-06-12
I guess it's talking about modules to completely understand the raid because you are working from live mode. Lets try the long way. Restart again in live mode with the cd, activate the raid again, and then try using chroot like this:
```
sudo mount /dev/md1 /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
```

Now you are like inside the installation. Install grub2 to /dev/sdc:
```
grub-install /dev/sdc
```

Exit chroot and unmount everything:
```
exit
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
```

Restart and grub2 should be on the MBR of /dev/sdc. Whether it boots correctly or not will depend on whether the grub.cfg is correct.

In the first command in the first block, I am assuming /dev/md1 is your root. If it's not, use the correct md device. Be very careful whether md0 or md1 is your swap or root. You need to mount the root device.

---

### Post by Messyhair42 on 2012-06-12
Thank you, I'll try this next. Do I still need to use the assembly command initially? And if grub.cfg isn't correct is it possible to edit it from live mode as well?

---

### Post by darkod on 2012-06-12
Yes, assembling the array would need to be done on each boot into live mode because no change is kept when you shut down, unless you have usb with persistence. That should keep the changes. Otherwise, everything you do in live mode is forgotten.

It's not advised to edit directly grub.cfg if it's not correct, but while you are doing the chroot, just in case, you can add this to the second block (before or after the grub-install):
```
update-grub
```

That will create updated grub.cfg.

---

### Post by Messyhair42 on 2012-06-12
I'm working from another installation of 12.04 and here is my latest result
```
root@Jason:/# grub-install /dev/sdc
/usr/sbin/grub-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!.
/usr/sbin/grub-setup: error: embedding is not possible, but this is required for cross-disk install.

```

Does this mean I need to reformat /sdc and /sdd and try again?
If so, the instructions I was using called for me to flag a certain partition as bootable, but in the partitioning screen it wouldn't let me do exactly that.

Edit: Could I just use my thumb drive as my boot sector, if I can get its instance of grub to point to the OS (which is already installed). It isn't necessary to have your bootloader on the same device as your OS, is it? It may not have automatically detected the OS, and running update-grub as root doesn't change it, but is there some other way to get it to work?

---

### Post by darkod on 2012-06-13
If your disks are with gpt table, you need a small partition with no filesystem and with the bios_grub flag set, so that grub2 can install properly.

You could have done that with the manual partitioner. Maybe it didn't allow you if you created the partition with a filesystem. You need to create the partition, and in the Use As select like "bootable BIOS partition" or similar. It should work with that.

In this case, to avoid reinstalling, you can select to install the grub2 bootloader to another disk like sda or sdb. Then set BIOS to boot from that disk. As long as the disk has msdos table it will not need the bios_grub partition.

---

### Post by Messyhair42 on 2012-06-13
I've got an insance of Fedora that has its own boot partition on another drive, can I set it up to use that? Fedora doesn't need it because I've got the thumb drive to boot into that. I've chainloaded into that before so I know it's bootable

Gnome partition editor tells me it's a 94MB partition on sda, as /sda3. so from my 12.04 disk; sorry, I don't know where to start.

---

### Post by darkod on 2012-06-13
You don't need a partition, we are talking about the bootloader only. Do the procedure in post #16 again but in the middle block instead of:
grub-install /dev/sdc

do something like:
grub-install /dev/sda

Then restart, set your BIOS to boot from /dev/sda disk, and that's it.

It's your choice where the bootloader is and which disk to boot from.

---

### Post by Messyhair42 on 2012-06-13
> **darkod said:**
> You don't need a partition, we are talking about the bootloader only. Do the procedure in post #16 again but in the middle block instead of:
grub-install /dev/sdc

do something like:
grub-install /dev/sda

Then restart, set your BIOS to boot from /dev/sda disk, and that's it.

It's your choice where the bootloader is and which disk to boot from.

does the grub-install command necessarily use free space (/sda also has a great deal of free space, but two OS's on it) I'd hate to disrupt anything I have on there?

---

### Post by darkod on 2012-06-13
Nope, it uses the very first cylinder on the hdd called Master Boot Record, MBR.

Linux will never take any space without asking you or disrupt your data.

It doesn't matter how much free space you have on a disk, or how many partitions, or no partitions at all. When installing a bootloader, it uses small amount of space on the very beginning of the hdd reserved for bootloaders. The MBR.

---

### Post by Messyhair42 on 2012-06-19
A typographical error caused the installation to be unsuccessful, but I tried again and got a successful installation. I configured my BIOS to boot to /dev/sda and I got a grub v 1.99 minimal BASH CLI. I didn't know what to do so tried booting back into ubuntu on my flash drive. It sends me into another CLI about my RAID being degraded asking if I would like to boot a degraded RAID. I haven't changed any hardware since I got the RAID installed. for one cycle my BIOS failed to recognize both 3.0 TB drives that make up the RAID but I've had similar things happen before and all it takes is a reboot. I couldn't boot to either flash drive without entering the degreaded RAID CLI. So I'm working from windows. again I've got grub on /dev/sda (which in all likelyhood the MBR of /sda used to contain window's own thing) I would be truly surprised if one of the drives has failed after a few weeks of installation when they aren't being used.

Is the RAID truly faulty at this point? if not how do I go about configuring my new instance of grub to recognize all my OS?

---

### Post by darkod on 2012-06-20
After you boot, what does:
```
cat /proc/mdstat
```

show?

---

### Post by Messyhair42 on 2012-06-20
error: file not found

---

### Post by darkod on 2012-06-20
You didn't specify if the degraded raid can boot or not. Because if you type that command at the grub prompt, it's normal that it will give an error.

If it manages to boot the degraded raid, it should display the raid info, not to give you that error.

If it fails to boot, you can work from live mode but you have to add the mdadm package first and assemble the array, since that is not included by default in live mode. It would be something like:
```
sudo apt-get install mdadm
sudo mdadm --assemble --scan
```

That should start the raid devices. After that you can try the cat /proc/mdstat.

---

### Post by Messyhair42 on 2012-06-21
```
jason@Jason:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sdd2[1] sdc2[0]
      2926359132 blocks super 1.2 [2/2] [UU]
      [>....................]  resync =  1.4% (42885888/2926359132) finish=383.5min speed=125290K/sec
      
md0 : active raid1 sdd1[1] sdc1[0]
      3905214 blocks super 1.2 [2/2] [UU]
      
unused devices: <none>

```

where md0 is swap space and md1 is /

I got my 12.04 flash drive to boot without a warning so that's where this is taken from.

---

### Post by darkod on 2012-06-21
As you can see, it's resyncing the array. It might take a long time depending on the size, it's barely at 1.4%.

Wait until it finishes the resync and see how it goes.

---

### Post by Messyhair42 on 2012-06-24
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active (auto-read-only) raid1 sde2[1]
      2926359132 blocks super 1.2 [2/1] [_U]
      
md0 : active (auto-read-only) raid1 sde1[1]
      3905214 blocks super 1.2 [2/1] [_U]
      
unused devices: <none>

```

after booting a degraded raid through my flash drive.

---

### Post by darkod on 2012-06-24
The previous mdstat showed the raid devices as sdc and sdd. This one shows sde with the other device removed.

Not only that it changes the devices raid members, it also seems to be dropping one of them.

Are your disks OK? Your system as a whole? You mentioned that BIOS failed to recognize one disk once. Or maybe more times?

---

### Post by Messyhair42 on 2012-06-25
BIOS dropping a drive happens, but it's not a consistant error, so I dont know how to diagnose it. If it truly is a problem over the next few cycles I'll make that it's own issue. So my first act should be to verify a properly configured RAID, right? once that's complete I can tackle the bootloader issue.

---

### Post by darkod on 2012-06-25
Have you tried with another sata cable?
Connecting the disk that is being dropped to another sata port?

I would connect the disks planned for raid in the first two ports anyway, so they would be sda and sdb.

---

### Post by Messyhair42 on 2012-07-17
I'm still here, after I got back from vacation I was too busy to do much of anything. I have swapped my cables around so the two raid drives are set as sda and sdb. however something still isn't right. gparted fails to recognize one of the 3TB drives, /dev/md1 as well as a 160GB drive

here is the output of ```
sudo fdisk -l
```
```
Disk /dev/sda: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      267350  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008e958

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux

Disk /dev/md0: 3998 MB, 3998939136 bytes
2 heads, 4 sectors/track, 976303 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Alignment offset: 3072 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md1: 2996.6 GB, 2996591751168 bytes
2 heads, 4 sectors/track, 731589783 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Alignment offset: 512 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/sde: 4022 MB, 4022337024 bytes
228 heads, 59 sectors/track, 584 cylinders
Units = cylinders of 13452 * 512 = 6887424 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003ef6e

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1         584     3926016   83  Linux
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 32, 33) logical=(0, 34, 43)
Partition 1 has different physical/logical endings:
     phys=(488, 227, 59) logical=(583, 195, 59)

Disk /dev/sdf: 16.0 GB, 16008609792 bytes
255 heads, 63 sectors/track, 1946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000845c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1        1216     9764864   83  Linux
/dev/sdf2            1217        1946     5863725    7  HPFS/NTFS

```

/sdb is my old backup drive. /sde and /sdf are my flash drives. I don't understand what it says about /dev/md1.

also here is the output of ```
cat /proc/mdstat
```
```
ersonalities : [linear] [multipath] [raid1] [raid0] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sdc2[0](F) sda2[1]
      2926359132 blocks super 1.2 [2/1] [_U]
      
md0 : active raid1 sdc1[0](F) sda1[1]
      3905214 blocks super 1.2 [2/1] [_U]

```

---

