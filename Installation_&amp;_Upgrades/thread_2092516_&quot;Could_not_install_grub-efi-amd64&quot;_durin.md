---
title: "&quot;Could not install grub-efi-amd64&quot; during  upgrade"
date: 2012-12-08
forum: Installation &amp; Upgrades
---

### Post by awr on 2012-12-08
Recieved the following error during the upgrade of Ubuntu 12.04 to 12.10.  Obviously I don't want to reboot as grub isn't installed and boot will fail.

 
```

Could not install 'grub-efi-amd64'
 The upgrade will continue but the 'grub-efi-amd64' package may not be  in a working state.  Please consider submitting a bug report about it.
 Subprocess install post-installation script returned error exit status 1


``` Then when trying to install grub-efi-amd64 manually, the following:
 

```
:/boot$ sudo apt-get install grub-efi-amd64
Reading package lists... Done
Building dependency tree
Reading state information... Done
grub-efi-amd64 is already the newest version.
grub-efi-amd64 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up grub-efi-amd64 (2.00-7ubuntu11) ...
/usr/sbin/grub-probe: error: cannot find a GRUB drive for /dev/mapper/isw_ddhbgcdgch_Borg_storage1.  Check your device.map.
/boot/efi doesn't look like an EFI partition.
Path `/boot/grub' is not readable by GRUB on boot. Installation is impossible. Aborting.
dpkg: error processing grub-efi-amd64 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of grub-efi:
 grub-efi depends on grub-efi-amd64 (= 2.00-7ubuntu11); however:
  Package grub-efi-amd64 is not configured yet.
 dpkg: error processing grub-efi (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 grub-efi-amd64
 grub-efi
E: Sub-process /usr/bin/dpkg returned an error code (1)
 
``````
:/boot$ lsb_release -rd
Description:    Ubuntu 12.10
Release:    12.10
ashley@borg1:/boot$ apt-cache policy ubiquity
ubiquity:
  Installed: (none)
  Candidate: 2.12.16
  Version table:
     2.12.16 0
        500 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) quantal-updates/main amd64 Packages
     2.12.14 0
        500 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) quantal/main amd64 Packages
 
```Boot-repair info script output (before running repair):  [http://paste.ubuntu.com/1418355/](http://paste.ubuntu.com/1418355/)



Boot-repair fails as grub-efi-amd64 not installed
 

Obviously I don't want to restart the computer as it won't boot if grub isn't installed.

EDIT:  Ok, didn't have a choice in restarting as the power went out.  As suspected computer wouldn't boot on restarting, booted from Ubuntu disk and ran boot-repair to get a booting system back.  This isn't really a fix though as it will only happen again next time grub is updated.

---

### Post by darkod on 2012-12-08
It's not that grub isn't installed, only that it wasn't upgraded, if I understand that right. In theory, ubuntu can boot even with previous grub versions.

Unfortunately, the only way to test that is to reboot, and there is a chance that it won't boot.

UEFI dual boot is still an enigma for most of us (especially me since I don't use UEFI and don't plan to). There are still issues with it, and specific things that you need to take care of.

On top of that, you are running fakeraid which only complicates things more, not making them easier.

This part is interesting:
> Setting up grub-efi-amd64 (2.00-7ubuntu11) ...
/usr/sbin/grub-probe: error: cannot find a GRUB drive for /dev/mapper/isw_ddhbgcdgch_Borg_storage1.  Check your device.map.
/boot/efi doesn't look like an EFI partition.

It seems to look for an entry in the device.map for Borg_storage1 which in fact is a partition. The 1 at the end means first partition. Did you install grub onto partition #1 instead of the MBR during the original instalation?

Grub2 shouldn't be installed on partitions, it doesn't fit on the partition boot sector. I am only guessing, but this error might mean that. If it was forced installed on a partition, and now it's trying to install the newer version there but without forcing it, it will fail.

The thing is that with uefi you don't even need grub that much I think, uefi boots in different way. But if you have to install it somewhere, I would choose the MBR of the array, not partition #1.

You can try checking where grub2 is pointing, with something like:
sudo dpkg-reconfigure grub-efi

If that shows only partition #1 and not the MBR of the array, this could be the issue. You will need to add grub2 also on the MBR of the array with:
sudo grub-install /dev/mapper/...Borg_storage

And after that reconfigure it with the dpkg-reconfigure and deselect partition #1, leave only the MBR. In text menus you select/deselect with the Space bar.

AFter that you can try installing the grub-efi-amd64 again. If it still complains about the device.map, try recreating it with:
sudo grub-mkdevicemap

---

### Post by oldfred on 2012-12-08
I do not know enough about RAID, but it looks more like a partition issue not efi per se.
> 
Disk /dev/sdb doesn't contain a valid partition table

Grub needs to parse partition tables to find partitions like  the efi partition to copy files into. If partition tables have errors then it fails. It also looks like a big part of Boot Info script did not post data probably for the same reasons.

I would look into partition table repairs, fsck or whatever is suggested for RAID systems.

---

### Post by darkod on 2012-12-08
On fakeraid, I'm not sure if this is an error or normal.

With software raid you know for sure that "normal" partition table should exist on the physical disks, and the raid is done on OS level.

But since the fakeraid is assembled first, I am not sure how fdisk should see the physical disks, because in theory the physical disks shouldn't even show in raid. But since it's fakeraid, they do show.

I recall having installed Server 10.04 LTS on a Dell server with proper hardware raid and I clearly remember the disk was recognized as simply /dev/sda. One single disk, the raid array. The proper HW card works as it should, it assembles the array itself and presents it as a single device to the OS. But with fakeraid it's not the same.

---

### Post by ronparent on 2012-12-08
I haven't followed the whole thread but I recently encountered something simular to:
> Setting up grub-efi-amd64 (2.00-7ubuntu11) ...
/usr/sbin/grub-probe: error: cannot find a GRUB drive for /dev/mapper/isw_ddhbgcdgch_Borg_storage1. Check your device.map. 
In my case this resulted because dmraid had not been installed with a new install of 12.10 to a fakeRAID partition. The solution that worked for me was to install it.

ie: > sudo mount <the raid partition you installed to> /mnt
sudo chroot /mnt apt-get install dmraid 

I don't know if this would resolve this problem, but, the error message that says a raid device cannot be found is often because the devices in /dev/mapper were not initiated during the boot.

---

