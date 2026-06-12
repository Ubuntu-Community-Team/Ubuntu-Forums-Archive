---
title: "Ubuntu installer needs some work"
date: 2024-05-02
forum: Installation &amp; Upgrades
---

### Post by bobwdn on 2024-05-02
I have been away from Ubuntu for various reasons for a few years (previous version install was: v20.04LTS.) I see lots of good changes in v24.04LTS. 

Although while installing v24.04 Cinnamon Remix I had issue with manual partitioning. 

There is no "guided partitioning" option to create a separate /home. So, I switched to "manual partitioner". After the switch I discover that I was having difficulty changing the partition scheme to what I needed. I was looking to have a GPT disk to boot UEFI and have a separate /home. I wish I had made better notes regarding what happened but, sorry, I did not. My bad! Graphically, the partitioner display 'appears' incorrect. Re-adjustment of the partition scheme (with the manual partitioner) resisted my change adjustments. 

I resorted to aborting the install and using a livecd with gparted to create my ssd partition scheme. I wanted a 1 Gb 'Free Space'. 160 Mb /boot/efi on a vfat partition. A 160 Gb 'root' partition on ext4. Swap space and finally a separate /home partition on the remainder of the ssd space. Returned to the Ubuntu installer, selected 'manual partitioning', added mount points and proceeded with the installation. All went well and soon an operational Ubuntu Cinnamon Remix OS.

I point this out (vaguely) with few details because in searching for a solution I saw many posts of similar installer issues back to v23.04. So, logically I am pretty sure the powers that be (at Ubuntu) are aware that there are issues (multiple issues apparently) with the installer partitioner. The old partitioner (in v20.04) worked great! So, Ubuntu people, let's get into these issues and make corrections, please! If it works, don't break it and if you improve, indeed improve and make it work better, NOT worse, please.

Sorry, my two cents for what it's worth.

---

### Post by TheFu on 2024-05-02
I've had problems setting up the manual partitioning in a way that was acceptable to the installer too.  My only guess is they installer team figure if you are going to do manual installation, then you know which partitions are required, how they need their flags set, what size to make each and which file system types are required.

With Lubuntu a few days ago, I tried to manually setup LVM and failed. Couldn't figure out the requirements to get booting and LVM with the minimal number of partitions created.  Eventually, I gave up (it was just a toy install) and did the "next-->next-->next-->next-->next-->next-->next-->next-->" install using all defaults.

In previous installs, I setup a number of partitions, 2 that I don't really know if they are required, but wasting 1MB for them wasn't a big deal and since I'm using GPT, there's no 4 primary partition limitation that used to get in the way before. I will post the partitions I've used that worked in 20.04. 
```

# Set some variables to be used below:
  export DEV=/dev/sda

  # Change sizes below for your needs 
  export SZ_EFI="50M"
  export SZ_BOOT="700M"
  export SZ_root="10G"   # for servers - can be expanded later
  export SZ_root="35G"   # for desktops - can be expanded later
  export SZ_home="10G"   # for desktops - can be expanded later
  export SZ_swap="1G"    # for servers
  export SZ_swap="4.1G"  # for desktops
  export SZ_var="2G"     # for servers (no snaps) - can be expanded later
  export SZ_var="10G"    # for desktops  - can be expanded later
  export SZ_tmp="2G"     #  May need to increase this if lots of snaps are used or downloads go to /tmp/

# the volume group name - should be unique. Handy if it is unique across ALL computers you manage.
  export VG_NAME=vg00

# Clear and create the partitions
  sgdisk --clear $DEV   # create fresh GPT partition table on the device
  
  sgdisk --new=1:0:+1M        --typecode=0:ef02 --change-name=0:GRUB   $DEV  # BIOS Boot Partition (legacy)
  sgdisk --new=2:0:+${SZ_EFI}  --typecode=0:ef00 --change-name=0:EFI-SP $DEV  # for /boot/efi
  sgdisk --new=3:0:+${SZ_BOOT} --typecode=0:8300 --change-name=0:boot   $DEV  # for /boot
  sgdisk --largest-new=4 --typecode=0:8e00 --change-name=0:LVM    $DEV  # for the LVM PV/VG and multiple LVs

  sgdisk --typecode=1:ef02 --typecode=2:ef00 --typecode=3:8300 --typecode=4:8e00 $DEV
  sgdisk --change-name=1:GRUB --change-name=2:EFI-SP --change-name=3:boot \
         --change-name=4:LVM $DEV
  sgdisk --hybrid 1:2:3:4 $DEV
  sgdisk --print $DEV

# Create the LVM objects - PV, VG, and multiple LVs.
  pvcreate ${DEV}4
  vgcreate ${VG_NAME} ${DEV}4
  lvcreate -L ${SZ_swap} -n swap ${VG_NAME}
  lvcreate -L ${SZ_root} -n root ${VG_NAME}
  lvcreate -L ${SZ_var}  -n var ${VG_NAME}
  lvcreate -L ${SZ_tmp}  -n tmp ${VG_NAME}
  lvcreate -L ${SZ_home} -n home ${VG_NAME}
  lvscan

# time to format with file systems
  mkfs -t ext2 ${DEV}1  # not sure what this is about.
  mkfs -t vfat ${DEV}2  # /boot/efi
  mkfs -t ext2 ${DEV}3  # /boot
  mkswap  /dev/${VG_NAME}/swap  # swap (this was activated by the installer)
  mkfs -t ext4 /dev/${VG_NAME}/root  # / 
  e2label /dev/${VG_NAME}/root root
  
  mkfs -t ext4 /dev/${VG_NAME}/home  # /home 
  e2label /dev/${VG_NAME}/home home
  
  mkfs -t ext4 /dev/${VG_NAME}/var  # /var
  e2label /dev/${VG_NAME}/var  var
  
  mkfs -t ext4 /dev/${VG_NAME}/tmp  # /tmp
  e2label /dev/${VG_NAME}/tmp  tmp
```

I use these mount options for the specific file systems:
```
  # Mount options
  /home nodev,nosuid
  /tmp  nodev,nosuid,noexec
  /var  nodev,nosuid,noexec
```
  
So, you can set the sizes to what you like.  I'm using LVM, all the PV, VG and LV stuff is for LVM.
I use that script as the base, then slightly modify it, usually just the sizes, for each system as needed.  I run it after starting the installer, but before getting to the "Do Something Else" option by switching to a different non-GUI console screen in the installer, installing ssh and pulling the base script over to the installation environment.  If I'm in the "Try Ubuntu" mode, this can be done using a graphical environment.

From parted -l, here's the partitions created by the sgdisk commands:
```
Model: Samsung SSD 980 1TB (nvme)
Disk /dev/nvme0n1: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name    Flags
 1      1049kB  2097kB  1049kB  ext2         GRUB    bios_grub
 2      2097kB  54.5MB  52.4MB  fat16        EFI-SP  boot, esp
 3      54.5MB  789MB   734MB   ext4         boot
 4      789MB   1000GB  999GB                LVM     lvm

```

Inside the installer, I just need to connect the mount location to the newly created partitions and LVs, then figure out which absolutely must allow the installer to re-format and check that box when necessary.  The resulting layout looks like this:
```
NAME                             TYPE  FSTYPE              SIZE FSAVAIL FSUSE% LABEL       MOUNTPOINT
nvme0n1                          disk                    931.5G                            
&#9500;&#9472;nvme0n1p1                      part  ext2                  1M                            
&#9500;&#9472;nvme0n1p2                      part  vfat                 50M   43.9M    12%             /boot/efi
&#9500;&#9472;nvme0n1p3                      part  ext4                700M  339.8M    42%             /boot
&#9492;&#9472;nvme0n1p4                      part  LVM2_member       930.8G                            
  &#9500;&#9472;vg01-swap01                  lvm   swap                4.1G                            [SWAP]
  &#9500;&#9472;vg01-root01                  lvm   ext4                 35G     25G    22%             /
  &#9500;&#9472;vg01-var01                   lvm   ext4                 20G     14G    23%             /var
  &#9500;&#9472;vg01-tmp01                   lvm   ext4                  4G    3.6G     1% tmp01       /tmp
  &#9492;&#9472;vg01-home01                  lvm   ext4                 20G    9.2G    48% home01      /home

```
Obviously, there are slight differences in sizes and names than the script would create.  You can also see that the LVM partition is 930GB, but I'm using less than 200GB of that total space.  LVM allows growing LVs while the file system is active and busy, should that be needed. Having most of the VG unused provides all sorts of flexibility.  I actually have other LVs that I removed from the output for virtual machines and linux containers.  Felt that showing those in the output above when they aren't in the script anywhere could be confusing for some people, especially if they aren't used to using LVM at all.

I wish Canonical would just steal the disk layout tool from the CentOS installer from 10 yrs ago for the "do something else" choice.  That was very capable and clear.

---

### Post by Dennis N on 2024-05-02
The newer "Ubuntu Desktop Installer" does not fully support LVM installations. The only way to get an LVM install is to use the erase and install option, and choose LVM from the advanced options. 

If you need to use an existing LV for the installation, the manual install screen cannot detect it for the installation. You are out of luck.

It has been so since the appearance of this new installer in Ubuntu 23.04 (which also offered an alternate legacy ISO using the old installer).

There has been discussion of this deficiency off and on since Ubuntu 23.04 first appeared. Bug reports have been filed. Hopes of a fix in the new LTS version have proved to been in vain. No action has been taken.

The only way I could test 24.04 here was to use a virtual machine.

---

### Post by TheFu on 2024-05-02
Lacking LVM at install time is sufficient reason why 24.04 won't see production here. Lots of enterprises will make similar choices or they will be forced to use ZFS (which isn't necessarily bad) before they are ready.

---

### Post by MAFoElffen on 2024-05-02
I don't even want to start with this subject.

I have turned in many bug reports against the new installer, since they went to it with Lunar 23.04.

Most of it would be censored here.

RE: [https://bugs.launchpad.net/ubuntu-desktop-installer/+bug/2014977](https://bugs.launchpad.net/ubuntu-desktop-installer/+bug/2014977)

Absolutely Ridiculous that they ignored that, and said they would not fix it... I will not let that die there. I will keep pushing until they can no longer ignore me. If they tell me to refile it, I will... I I will be on a mission to get as many people that I can to subscribe to it, so they cannot ignore it.

---

### Post by TheFu on 2024-05-03
You might want to edit that last bug entry. You left out a "not" that is important!
Can't they just steal the partitioning method that CentOS had in 2015 and use it?  Why is this so hard to keep LVM working? It isn't like the code is unstable.

---

### Post by MAFoElffen on 2024-05-03
The "new" partitoner choice they made... On Ubuntu Discourse, they said the reason they picked that one, was because it recgnized partitions with Bit-Locker(???)

Really? BitLocker is Windows only!!! That choice makes no sense to me. Yes, maybe they can now make it easier to install alongside of Windows, with BitLocker turned on (I was just telling people to suspend BitLocker during the install, which solves that), but... In making that choice, they lost all abilities to recognize all Linux filesystems & Volume Managers. That same announcement said they would be working to improve that partitioner. They haven't. ...and that announcement was over a year and ago.

Start to understand a bit of that frustration? Jeeze.

---

### Post by aljames2 on 2024-05-03
> **MAFoElffen said:**
> Start to understand a bit of that frustration? Jeeze.

I am still on 22.04 so i haven’t seen this yet but I understand this is an issue. I also do custom partitions & set up LVM before running the installer.  I will also need to follow this more closely before changing versions.  Thanks for speaking up about it, I had not realized this yet.

---

