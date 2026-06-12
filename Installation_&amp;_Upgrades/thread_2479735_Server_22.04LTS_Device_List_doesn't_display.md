---
title: "Server 22.04LTS Device List doesn't display"
date: 2022-10-04
forum: Installation &amp; Upgrades
---

### Post by geebee75 on 2022-10-04
While trying to create either new MD or LVM devices during setup, the list of devices in the "Create software RAID" box (or LVM) is blank, however they are present.

You can move the grey selector bar up and down. It will show nothing whether or not the bar is on a selection or not. However pressing Enter on any of the blank lines seems to select things.

I've tried two different monitors. Any suggestions?

---

### Post by TheFu on 2022-10-05
If you do a single-disk basic LVM setup, then you can create mirrored LVs post-install with a few commands.

This is all post-install, after choosing to let LVM use the entire disk as it likes.  Normally, I setup the LVM VGs and LVs on 1 disk the specific way I like. Something like this:
```

$ lsblk -e 7 -o name,size,type,fstype,label,mountpoint

nvme0n1                    465.8G disk                    
&#9500;&#9472;nvme0n1p1                   50M part vfat    EFI        /boot/efi
&#9500;&#9472;nvme0n1p2                  600M part ext4               /boot
&#9492;&#9472;nvme0n1p3                  465G part LVM2_me            
  &#9500;&#9472;vg00-swap                4.1G lvm  swap               [SWAP]
  &#9500;&#9472;vg00-root--00             35G lvm  ext4               /
  &#9500;&#9472;vg00-var                  35G lvm  ext4               /var
  &#9492;&#9472;vg00-home                 25G lvm  ext4    home       /home
```
Then I do the install and "do something else" in the storage area, selecting the different partitions and LVs for formatting and mount points above.  I made /var much larger in that example for a specific need. Normally, it would be 2G in size.

Then let the install finish.

Patch, reboot, install any proprietary GPU drivers (nvidia only) and add some of the key software packages I want.  While those steps are running, I'd setup a 2nd drive with PV and VG, then use the 'sudo lvconvert  --mirrors +1 ....' command to have the existing LVs get mirrored.  /boot and /boot/efi wouldn't be mirrored.  Those need to be manually copied - probably using 'rsync' to ext2 and FAT32 partitions on the other disk.  Manually doing that will be part of my world going forward after every kernel or grub update.  There are how-to guides for this stuff, so I won't repeat those here.

mdadm is a little old school. I only use it for legacy systems that already have mdadm running.  New storage doesn't use it.  And for data (not OS) redundancy, I'd use ZFS instead.

And always remember that RAID1 or mirroring never replaces the need for excellent, automatic, daily, versioned, backups.  Backups solve 1001 problems, including corrupted RAID arrays.  RAID1 solves just 2 issues that most people don't have.

For fun, I spun up a 22.04 server with LVM.  It is a very simple, small, setup.

```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 22.04.1 LTS
Release:        22.04
Codename:       jammy

$ lsblk -e 7 -o name,size,type,fstype,label,mountpoint
NAME                 SIZE TYPE FSTYPE      LABEL MOUNTPOINT
vda                   15G disk                   
&#9500;&#9472;vda1                 1M part                   
&#9500;&#9472;vda2               768M part ext4              /boot
&#9492;&#9472;vda3              13.2G part LVM2_member       
  &#9500;&#9472;vg--00-lv--0      10G lvm  ext4              /
  &#9492;&#9472;vg--00-lv--swap    1G lvm  swap              [SWAP]
```
So, I need to add another 15G disk to this VM.  Give me a second.  Ok, done.
```
NAME                 SIZE TYPE FSTYPE      LABEL MOUNTPOINT
vda                   15G disk                   
&#9500;&#9472;vda1                 1M part                   
&#9500;&#9472;vda2               768M part ext4              /boot
&#9492;&#9472;vda3              13.2G part LVM2_member       
  &#9500;&#9472;vg--00-lv--0      10G lvm  ext4              /
  &#9492;&#9472;vg--00-lv--swap    1G lvm  swap              [SWAP]
vdb                   15G disk                   
```
Time for some fdisk/parted/gdisk work.  Let's copy the GPT from a --> b and randomize the vdb GUIDs:
```
sudo sgdisk -R /dev/vdb /dev/vda
sudo sgdisk -G /dev/vdb
# Now we have this ... vda and vdb are the same:
$ lsblk -e 7 -o name,size,type,fstype,label,mountpoint
NAME                 SIZE TYPE FSTYPE      LABEL MOUNTPOINT
vda                   15G disk                   
&#9500;&#9472;vda1                 1M part                   
&#9500;&#9472;vda2               768M part ext4              /boot
&#9492;&#9472;vda3              13.2G part LVM2_member       
  &#9500;&#9472;vg--00-lv--0      10G lvm  ext4              /
  &#9492;&#9472;vg--00-lv--swap    1G lvm  swap              [SWAP]
vdb                   15G disk                   
&#9500;&#9472;vdb1                 1M part                   
&#9500;&#9472;vdb2               768M part                   
&#9492;&#9472;vdb3              13.2G part                   
```

Now it is time for some LVM2 work ... the good news is that lvm is lvm is lvm - the distro doesn't matter.  So, find a guide regardless of the distro and follow it. [https://askubuntu.com/questions/55968/add-new-hard-drive-to-mirror-existing-lvm-drive-with-raid1](https://askubuntu.com/questions/55968/add-new-hard-drive-to-mirror-existing-lvm-drive-with-raid1) seems short and reasonable. Sure, it is 11 yrs old, but that doesn't matter. LVM is LVM is LVM on Linux.
```
sudo pvcreate /dev/vdb3  # create a PV
sudo vgextend vg-00 /dev/vdb3 # extend the existing vg-00 to use the new storage device PV 
```
And now for the big banana:

```
sudo lvconvert -m1 /dev/vg-00/lv-0  /dev/vdb3
Are you sure you want to convert linear LV vg-00/lv-0 to raid1 with 2 images enhancing resilience? [y/n]: y
  Logical volume vg-00/lv-0 successfully converted.
```
I woon't be doing the swap too - I don't plan to harm my NVMe SSD (this is all running inside a VM with all virtual storage devices coming from the same SSD, so it is pretty useless for redundancy, but good to learn.
And the proof that is it mirrored. It has been less than a minute, BTW.
```
$ sudo lvs
  LV      VG    Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  lv-0    vg-00 rwi-ao**r**--- 10.00g                                    **100.00          **
  lv-swap vg-00 -wi-ao----  1.00g                             

$ lsblk -e 7 -o name,size,type,fstype,label,mountpoint
NAME                       SIZE TYPE FSTYPE      LABEL MOUNTPOINT
vda                         15G disk                   
&#9500;&#9472;vda1                       1M part                   
&#9500;&#9472;vda2                     768M part ext4              /boot
&#9492;&#9472;vda3                    13.2G part LVM2_member       
  &#9500;&#9472;vg--00-lv--swap          1G lvm  swap              [SWAP]
  &#9500;&#9472;vg--00-lv--0_rmeta_0     4M lvm                    
  &#9474; &#9492;&#9472;vg--00-lv--0          10G lvm  ext4              /
  &#9492;&#9472;vg--00-lv--0_rimage_0   10G lvm                    
    &#9492;&#9472;vg--00-lv--0          10G lvm  ext4              /
vdb                         15G disk                   
&#9500;&#9472;vdb1                       1M part                   
&#9500;&#9472;vdb2                     768M part                   
&#9492;&#9472;vdb3                    13.2G part LVM2_member       
  &#9500;&#9472;vg--00-lv--0_rmeta_1     4M lvm                    
  &#9474; &#9492;&#9472;vg--00-lv--0          10G lvm  ext4              /
  &#9492;&#9472;vg--00-lv--0_rimage_1   10G lvm                    
    &#9492;&#9472;vg--00-lv--0          10G lvm  ext4              /

```
Since the LV didn't change names, the /etc/fstab doen't need to be changed.  I usually modify the fstab mount device to be something useful, not the default ... let's see ...
```
$ more /etc/fstab 
**/dev/vg-00/lv-0 / ext4 defaults 0 1**
/dev/vg-00/lv-swap none swap sw 0 0
#
# /boot was on /dev/vda2 during curtin installation
UUID=59ab80e1-0dc0-4d67-81f0-b62f14ef50dd /boot ext4 defaults 0 1
```

And now for the always critical test .... a reboot.  Give me a second.  I suppose you'll need to trust me, but it worked.

On a real server, I'd have LVs for /home, /, /var,  .... all those things at the top of this post ... and more.  I tend to make specific LVs for specific needs.  For example, the system at the top of the post is a media server running jellyfin.  All the jellyfin metadata is stored in a specific LV. Here's the df -Th for that storage:
```
/dev/mapper/istar--8TB--B-jellyfin_varlib   ext4   89G  6.9G   77G   9% /var/lib/jellyfin

# and the fstab line that mounts it:
/dev/istar-8TB-B/jellyfin_varlib /var/lib/jellyfin        ext4 noatime,nodev,nosuid 0 1
```
I hope swapping between two different computers, both using LVM isn't confusing.

Back to the test virtual machine ... I would need to 'mkfs' for the /boot and /boot/efi on vdb now ... then use 'rsync' to copy everything over in 2 rsync commands.  These won't be used, unless I specifically request to boot from them in the BIOS.  Heck, I'm curious now.  I can see issues with having 2 FAT32 EFI boot areas inside the same system.  If I really needed to boot to avoid the failed drive, I'd break the mirror and unplug the failed disk to prevent confusion.  Probably would need to use an EFI boot mgr tool to select the boot partition to be used.   Alas, my virtual machine uses BIOS booting, not EFI. Sorry.

---

### Post by geebee75 on 2022-10-05
Thanks for that, was very helpful and was able to get things going after initial install as you said.

I've always used standard RAID and never LVM until now. So now I'm finally getting around to learning it. So far it's a pain, and RAID5 failover doesn't work after reboot but that's a topic for another post I guess - and I'll do next. :)

BTW that lsblk -e 7 -o name,size,type,fstype,label,mountpoint command was handy, didn't know that.

---

### Post by TheFu on 2022-10-05
> **geebee75 said:**
>  BTW that lsblk -e 7 -o name,size,type,fstype,label,mountpoint command was handy, didn't know that.

Make it an alias!  I certainly don't type that ... or my df/du commands with options either.  I've posted my top 10 aliases in these forums a few times.
There are other options for lsblk ... like uuid which could also be helpful.

You probably don't really want RAID5 and definitely NOT for the OS/booting.  There are some bad failure modes that you can research.
If you want something like RAID5, use it for data storage only (never the OS/booting) and go with ZFS RAIDz or RAIDz2 instead.

---

