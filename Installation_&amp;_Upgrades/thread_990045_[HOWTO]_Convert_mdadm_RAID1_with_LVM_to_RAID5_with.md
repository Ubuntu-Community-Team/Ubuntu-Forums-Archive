---
title: "[HOWTO] Convert mdadm RAID1 with LVM to RAID5 without lose data"
date: 2008-11-22
forum: Installation &amp; Upgrades
---

### Post by edvar on 2008-11-22
Basically sharing my experience after spending a couple of hours on this. 

If you're not familiar with the concept, RAID is a way to provide fault tolerance in case one of your disks die and LVM is a technology that allows the flexibility of resizing volumes on the fly without reboot. LVM alone doesn't provide fault tolerance and RAID by itself doesn't provide flexibility. That's why LVM + RAID is the perfect combo.

My Ubuntu 8.10 system was installed on a LVM setup on top of a mdadm RAID1  with 2x 500Gb disks for fault tolerance. As you know, with RAID1 you lose one of the disks for mirroring purposes and the LVM allows me the flexibility to resize any of its logical volumes on the fly without any need of rebooting. As mentioned I have 4 LVM partitions on top of the mdadm RAID:

lv-root = 20GB
lv-home = 30GB
lv-var = 20GB
lv-media = rest of the disk

I was running out of space on the lv-media volume and for that reason I bought another 500Gb disk and installed on my box. Since I really like some fault tolerance I wanted to convert my RAID1 setup on a RAID5 setup without losing data (I didn't want to reinstall my system since it is on a perfect state and I didn't want to spend hours reconfiguring it). 

First of all I backed up my data and restarted my system using the Ubuntu Live CD. After that I installed LVM and MDADM and activated them on the Live CD environment since they're not on there by default:

> sudo -i
# apt-get install lvm2 dmraid mdadm
# modprobe dm-mod
# partprobe
# vgscan

I found out this tutorial on how to convert RAID1 to RAID5 without losing data on [http://scott.wallace.sh/?s=raid](http://scott.wallace.sh/?s=raid) so I followed the instructions:

[HTML]

Stop the array:

  # mdadm --stop /dev/md0

Overwrite the RAID1 metadata with the RAID5 metadata:

  # mdadm --create /dev/md0 --level=5 -n 2 /dev/hda1 /dev/hdb1
  mdadm: /dev/hda1 appears to contain an ext2fs file system
      size=1946592K  mtime=Sat Apr 14 07:18:32 2007
  mdadm: /dev/hda1 appears to be part of a raid array:
      level=1 devices=2 ctime=Sat Sep 17 16:17:45 2005
  mdadm: /dev/hdb1 appears to contain an ext2fs file system
      size=1946592K  mtime=Sat Apr 17 07:18:32 2007
  mdadm: /dev/hdb1 appears to be part of a raid array:
      level=1 devices=2 ctime=Sat Sep 17 16:17:45 2005
  Continue creating array? y
  mdadm: array /dev/md0 started.

At this point the RAID software decided it wanted to rebuild the array. Uh-oh, there goes my data&#8230; I quickly mounted /dev/md0 and had a look&#8230; all my data is still intact! Oh well, let the software do it&#8217;s thing. Who am I to argue?

Add in the third, new partition:

  # mdadm --add /dev/md0 /dev/hdd1

So far, so good. Once the rebuild is complete, grow the RAID5 onto the new partition: (NB: use the &#8211;backup-file option in case the grow is interrupted. It will allow a safe recovery.)

  # mdadm --grow /dev/md0 --raid-disks=3 --backup-file=/mnt/tmp/raid1-5.backup.file
  mdadm: Need to backup 128K of critical section ..
  mdadm: ... critical section passed.

I&#8217;m impressed that I&#8217;ve had no problems so far. The reshaping of the RAID5 from a 2 disk to a 3 disk array takes quite a while (about 6.5 hours for around 200GB of raw data) but the filesystem resize shouldn&#8217;t take anywhere near as long.[/HTML]

Great! So I thought I was done... I restarted the computer but grub wasn't finding my lv-root partition. I thought I had lost it all... but since I'm stubborn I decided to investigate further.

I restarted my box using the Live CD and installed/activated LVM and MDADM again. After running 'pvscan', 'vgscan' and 'lvscan' I found out my data was still there! I just needed to find a way to activate it after rebooting.

I noticed on the 'pvscan' output that the physical volume was still 500Gb even after I reshaped the RAID volume to 1Gb. So I ran:

# pvresize

and the physical volume was resized to 1 Gb. So was the volume group. 

I restarted again but same problem. My root logical volume wasn't recognized.

Booted again using the Live CD, installed/activated LVM and MDADM for the third time  and decided to remove all the configuration files of mdadm and lvm and reisntall them from scratch since maybe some garbage from my previous mdadm/lvm setup should still be on the kernel:

# mkdir /myraid
# mount /dev/VG/lv-root /myraid
# mount /dev/VG/lv-var /myraid/var
# mount /dev/sda1 /myraid/boot
# mount --bind /dev /myraid/dev
# mount -t devpts devpts /myraid/dev/pts
# mount -t proc proc /myraid/proc
# mount -t sysfs sysfs /myraid/sys
# chroot /myraid
# apt-get remove --purge mdadm lvm2 dmraid
# apt-get install mdadm lvm2 dmraid
# exit  

After that I rebooted the box and my system was back online like nothing ever happened. I resized my lv-media logical volume to twice its previous size and everything worked fine. 

Now I have a working 1Tb LVM with RAID5 setup and all my data is still there!!

---

### Post by edvar on 2008-11-26
I wrote this on another post but I believe it's also helpful:

> Just to add some more info, if you want to install Ubuntu from scratch with MDADM and LVM using the Live CD (not sure why LVM is not the default on Ubuntu as it is on Fedora):

(make sure you started your computer on the Live CD environment and your network connection is up)

BEFORE INSTALLATION

Plan your partitions and volumes before hand. For instance, in my case I have a md device /dev/md0 that handles my RAID 5 on 3x 500GB disks. This is my main Physical Volume PV. I added the PV /dev/md0 to a Volume Group called VG. On top of VG I have 4 logical volumes:

lv-root = 20GB for the / partition
lv-home = 50GB for the /home partition
lv-var = 20GB for the /var partition
lv-media = 650GB for my /MediaCenter partition with all my media files

The rest of the space is unallocated on VG so I can extend my LVs in the future, if needed.

Other than that my /boot partition is on a separate device /dev/sda1.

After you have your partition scheme figured out, execute these commands on the terminal:

# sudo -i
# apt-get install lvm2 mdadm system-config-lvm
# modprobe dm-mod
# fdisk (check fdisk man page on how to create the FD - Linux RAID Auto type partitions)
# partprobe
# mdadm --create (check mdadm man page and use the partitions created on the step above to create the /dev/md0 device)
# partprobe (again, just in case)
# system-config-lvm (for the LVM setup tool GUI or, if you feel adventurous, use the command line tools pvcreate, vgcreate and lvcreate)

INSTALLATION

Proceed with the normal installation. The Partitioner will recognize the LVM volumes and will format them with EXT3 accordingly.

AFTER INSTALLATION

Now you need to add the MDADM and LVM modules to your kernel so the RAID and LVM Volumes are recognized after reboot:

# mkdir /myraid
# mount /dev/VG/lv-root /myraid (assuming you have a LV for your root partition)
# mount /dev/VG/lv-var /myraid/var (assuming you have a LV for your rvar partition)
# mount /dev/sda1 /myraid/boot (assuming your boot partition is on /dev/sda1 - REMEMBER: BOOT PARTITIONS CAN NEVER BE ON MDADM OR LVM DEVICES)
# mount --bind /dev /myraid/dev
# mount -t devpts devpts /myraid/dev/pts
# mount -t proc proc /myraid/proc
# mount -t sysfs sysfs /myraid/sys
# chroot /myraid
# apt-get install mdadm lvm2
# exit

---

