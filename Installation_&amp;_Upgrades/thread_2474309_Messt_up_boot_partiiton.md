---
title: "Messt up boot partiiton?"
date: 2022-04-26
forum: Installation &amp; Upgrades
---

### Post by fox273 on 2022-04-26
So I have been playing with partitions (using lvm) in Ubuntu 20.04, and after incorrectly resizing the live root partition using lvresize, my system became unresponsive. Not a big issue, I had backups, so I went for a fresh install.

The goal of the entire operation is to get a 100GB root partition, and a 900GB home partition. During the reinstall, I again chose the option to setup the partition automatically, resulting in a 1 TB root partition. After the install, I restarted Ubuntu from the USB image, and not from disk, and resized the root partition using this [https://unix.stackexchange.com/a/544965](https://unix.stackexchange.com/a/544965) method. I also added a second logical volume.

I restarted my PC, selected the fresh install from the boot menu, and the PC wouldn't boot.

I reinstalled the system from the usb, this time trying to use the existing partitions(100GB and 900GB) to mount on / and /home, plus selecting the swap and boot partitions. The installation went smoothly, but after restart the boot loader runs, but after that I only see the MSI logo on screen ( I have a MSI motherboard).

I reinstalled, using the automatic partitioning using lvm for the entire disk, this time I didn't touch the partitioning after install, same result. I get to the boot loader, select Ubuntu, and I see the MSI logo. No OS.

Perhaps I somehow messed up the boot partition in this process? Maybe the reinstall doesn't touch the existing boot partition? Is there any way to debug this?

EDIT: I started ubuntu in safe mode. efsck wouldn't run. The system summary stated that the physical volume was not ok (bad). I continued, and ubuntu loaded fine. I checked the SMART data of my NVME disk, I didn't see an issue. Reboot went ok. So I am happy that ubuntu runs, but still a little worried.

---

### Post by TheFu on 2022-04-26
When I want to customize the LVs during installation, I boot using a Try Ubuntu/Installer flash drive, and use either of those choices.
In Try Ubuntu mode, I'll install ssh, so I can pull a partitioning and LVM creation script from a different machine using scp, then tweak that script just a bit inside the Try Ubuntu environment, then run it.  From a high level (it isn't safe for general use), it is based on [Https://ubuntuforums.org/showthread.php?t=2465735&p=14053144#post14053144](Https://ubuntuforums.org/showthread.php?t=2465735&p=14053144#post14053144) and :
wipes the entire target disk,
creates a new GPT partition table,
creates some partitions and LVs:
```
# Part  mount           part_type       fs_type size
1       /boot/efi       EFI             fat32   50MB (dual+boot needs more)
2       /boot           LINUX           ext2    600MB
3       LVM             LVM             na      Remaining storage
 root   /               LV              ext4    35GB
 home   /home           LV              ext4    40GB
 var    /var            LV              ext4    2GB
 swap   swap            LV/SWAP         swap    4.1GB
```
100G is much too large for a root LV. almost 3x too large. Wasteful, especially with LVM.

The biggest tip I have for using LVM is to never allocate more than is needed for each LV for the next few months.  Just because you have 1TB, that doesn't mean you should allocate it now.  Start with 50G.  Expanding an LV is 5 seconds.  Plus, with some empty space inside the VG, you can use the most powerful aspects of LVM - snapshots.  If you've allocated all the VG storage to active LVs, you've screwed yourself.  And if the storage device is an SSD, try to leave 20% empty so the SSD controller can better manage endurance, drastically increasing the SSD lifespan.

The tools in the script are:```

  export DEV=/dev/sda
  export VG_NAME=vg00
  sgdisk --clear $DEV   # create fresh GPT partition table on the device

  sgdisk --new=1:0:+1M   --typecode=0:ef02 --change-name=0:GRUB   $DEV  # BIOS Boot Partition (legacy)
  sgdisk --new=2:0:+50M  --typecode=0:ef00 --change-name=0:EFI-SP $DEV  # for /boot/efi
  sgdisk --new=3:0:+600M --typecode=0:8300 --change-name=0:boot   $DEV  # for /boot
  sgdisk --largest-new=4 --typecode=0:8e00 --change-name=0:LVM    $DEV  # for the LVM PV/VG and multiple LVs
# Then
  pvcreate ${DEV}4 
  vgcreate {VG_NAME} {DEV}4
  lvcreate -L 4.1G -n swap ${VG_NAME}
  lvcreate -L 15G -n root ${VG_NAME}
  lvcreate -L 2G  -n var ${VG_NAME}
  lvcreate -L 10G -n home ${VG_NAME}

  # create the mapper links
  lvscan

  # lay down some file systems
  mkfs -t ext2 ${DEV}1  # not sure what this is about.
  mkfs -t vfat ${DEV}2  # /boot/efi   ----- check that this is FAT32 during the installer, I've seen it as FAT16.
  mkfs -t ext2 ${DEV}3  # /boot
  mkswap  /dev/${VG_NAME}/swap  # swap (this was activated by the installer)
  mkfs -t ext4 /dev/${VG_NAME}/root  # /
  e2label /dev/${VG_NAME}/root root

  mkfs -t ext4 /dev/${VG_NAME}/home  # /home
  e2label /dev/${VG_NAME}/home home

  mkfs -t ext4 /dev/${VG_NAME}/var  # /var
  e2label /dev/${VG_NAME}/var  var

```
Now, go into the installation task ... and for the disk layout - "Do Something Else".  The installer will show our partitions and LVs, so we just need to connect those with the mount location.
Be certain to NOT reformat any of the file systems - we already did that and added labels, except the EFI one, which may show as FAT16, but must be FAT32 to be valid.  The labels make it clear and easier to know which is what for the next 5 yrs this OS will live.

Practice increasing the size of /var.  Perhaps add 500MB to it? See it is nearly instant to increase - 1 command. That's it.  If you do virtual machines, then most VM managers can use LVM storage directly, so the VM gets a block device as a dedicated LV. It shouldn't be mounted in the hypervisor host.  Now we can make snapshots of entire VMs while those VMs keep running.  It is also very useful for backing up the hostOS while it keeps running. Create snapshots for each LV, sized to hold any changes while the backups occur.  Mount the named snapshots and backup those locations. We get a perfect copy, 100% quiesced, no data corruption, even on the busiest DB servers.

If we find that we need other storage areas for new needs - perhaps a data LV to share with multiple users - then we can create a new LV, mount it, and setup the permissions to allow the specific usernames write access through their group membership. This also can limit how much storage any project gets easily without using complex quotas.

BTW, I used to use 25G for the root LV, but 20.04 bloat made me change to 35G.  Seems they started forcing a swapfile, which can be removed post-install. Just don't forget to remove the /swapfail.img line in the /etc/fstab too. That will return the multi-GB of that file.  Arrrg.  If I've setup a swap LV or partition, I don't want a swapfile - Canonical!  Actually, I never want a swapfile, but different people make different choices. With GPT, it isn't like we have any real limit on the number of partitions. With LVM, we definitely don't have any limits on the number of LVs.

In a play install of 22.04 server, I noticed that the installer wants /boot to be 1.75G!!!   Are they crazy!  Srsly!!!  Post install, it was using about 130MB.  On a 16G storage chromebook, ubuntu is just trying to make it so we can't use their OS with those choices, er ... and bloated snaps.

---

