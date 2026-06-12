---
title: "Zfs - separate home pool (hpool)"
date: 2023-11-01
forum: Installation &amp; Upgrades
---

### Post by aljames2 on 2023-11-01
In using the OpenZFS manual install of Ubuntu root on zfs 22.04, there is no explanation how to install home on a separate pool. I have it done, but I think my steps for this are a bit out of order because I had some trouble with /home after reboot but that is fixed now.  My question is whether the pool & dataset create commands for hpool can be done in-stride with setting up bpool & rpool, or if this should be created later, after exiting chroot.  

There is also whether we need to do the zed on /etc/zfs/zfs-list.cache/(for hpool) ?  Does every pool need a zfs-list.cache created?

---

### Post by MAFoElffen on 2023-11-02
In the pool and dataset creates section, after creating, in this order zpools rpool, bpool, hpool, dpool, etc. Then create the dataset filesystem container (rpool/ROOT, bpool/BOOT/hpool/USERDATA, then all the filsystem dataset mounpoints...

So greatly summarized
```

# You are already root. and have already created the rpool and boot...
zpool create -o canmount=o yes -o mountpoint=/home.-R /mnt hpool $DISK

```
Then you continue on setting rpool datasets, then bpool datsets, then after that finish the added pool datasets
```

zfs create -o canmount=no -o mountpoint=none hpool/USERDATA/  
zfs create -o canmount=yes -o mountpoint=/home hpool/USERDATA/ubuntu_#UUID  

```
Rinse, and repeat for all your other data pools and dataset bases for them

That way, the root is there first, then the mountpoints attached to that, off from the root...

Then you populate the system image within that framework. Then you choot into that systems to finish installing and configuring that.

---

### Post by aljames2 on 2023-11-02
Thanks, I follow you.
If also, I do another pool for kvm stuff, images & ISOs, would I also set up that framework at that time as well?  I ask because at this point we have not yet installed kvm and we may want to have the dataset mountpoints refer to locations that don&#8217;t exist yet until kvm is installed.

---

### Post by MAFoElffen on 2023-11-02
My laptop ran the battery completely down, or I would post one of my recipe's to use as an example.. But here is the jist of what I do for that....

creating rpool, and temporarily it at /mnt, that is the base of the framework you have created, so think of /mnt=/... When you then create bpool and temp mount that at /mnt, / already exists there, so mounts in that base at /mnt (/boot). Same with home at /mnt (/home)...

For a pool beyond those, I then manually create enough of a directory tree to hang my other ZFS mounts to, Such as this (as root). I'm not sure this is really required, but I do this to cover my behind in case it is... The premise is that I start biullding my basic directory tree within the root rpool. I have done the same for other Volume managers, and storage containers, such as LVM, BTRFS, LUKS, mdadm, etc...
```

mkdir /mnt/data
mkdir /etc
mkdir//etc/libvirt
mkdir /home/mafoelffen
mkdir /home/Downloads/
mkdir /home/Downloads/ISO
mkdir /var/lib/libvirt

```
I name my pool for KVM as kpool. Easy for me to remember. The reason I create 3 separate datasets for them within that pool, is there are 2 places KVM installs things. that I want to keep track of, for the VM machine conigs, and Vm disk images... Then a 3rd for my ISO library. I separate it out into kpool, with kpool in a directory in a partition on a separate disk, so that later, I can migrate all my KVM important stuff, just by an export form the old system, with an import into the new. Or if I want to replicate that on a new system... send/receive a snapshot to the new system, then import it.

Before KVM is installed, then the framework exists to install those things within that. I will also use rsync to populate those from other pools or remote machines, if that is what I want to do. ZFS make things easy and flexible.

---

### Post by MAFoElffen on 2023-11-02
This recipe was my laptop, which I did in steps, instead of all at once, but good for ideas on how what I described above works:
```

#!/bin/bash

## Migratio for my Lenovo ThinkPad T520
#  I had rsync'ed it to a drive to redo the underlying volume manger. 

sudo su -i

apt install zfs-dkms zfs-initramfs

ls -la /dev/disk/by-id

$DISK=/dev/disk/by-id/ata-Samsung_SSD_870_QVO_2TB_S6R4NJ0R624350W

gdisk $DISK

## Recipe details
# Name                  Layout    Code  Type              
#  |_ boot_grub         1:+750M   EF00  ESP
##
#  |_ Swap              0:+3G     BF02  Solaris Swap
#  |_ rpool/ROOT        0:+5G     BFOO  Solaris Root
#  |_ homepool/USERDATA 0:0       BFO%  Solaris Home

## Existing
#Number  Start (sector)    End (sector)  Size       Code  Name
#   1            2048         1128447   550.0 MiB   EF00  EF
#   2         1128448         1390591   128.0 MiB   0C01  Mi
#   3         1390592      1888827391   900.0 GiB   0700  WIN10
#   4      3842101248      3844114431   983.0 MiB   2700  
#   5      3844114432      3907028991   30.0 GiB    2700  

ls -lah /dev/disk/by-id/
DISK=/dev/disk/by-id/ata-Samsung_SSD_870_QVO_2TB_S6R4NJ0R624350W

## Add partitions
# For Linux Swap
sgdisk     -n6:0:+32G    -c6:swap -t6:BF02 $DISK

# For bpool boot
sgdisk     -n7:0:+2G     -c7:bpool  -t7:BE00 $DISK

# For rpool root
sgdisk     -n8:0:+500G   -c8:rpool  -t8:BF00 $DISK

# For homepool home
sgdisk     -n9:0:0       -c9:hpool  -t9:BF05 $DISK

#
#Number  Start (sector)    End (sector)  Size       Code  Name
#   1            2048         1128447   550.0 MiB   EF00  EF
#   2         1128448         1390591   128.0 MiB   0C01  Mi
#   3         1390592      1888827391   900.0 GiB   0700  WIN10
#   4      3842101248      3844114431   983.0 MiB   2700  
#   5      3844114432      3907028991   30.0 GiB    2700  
#   6      1888827392      1955936255   32.0 GiB    BF02  swap
#   7      1955936256      1960130559   2.0 GiB     BE00  bpool
#   8      1960130560      3008706559   500.0 GiB   BF00  rpool
#   9      3008706560      3842101247   397.4 GiB   BF05  hpool
#

zpool create \
    -o ashift=12 \
    -o autotrim=on \
    -O acltype=posixacl -O xattr=sa -O dnodesize=auto \
    -O compression=lz4 \
    -O normalization=formD \
    -O relatime=on \
    -O canmount=off -O mountpoint=/ -R /mnt \
    rpool $DISK-part8

# Not yet
zpool create \
    -o ashift=12 \
    -o autotrim=on \
    -o cachefile=/etc/zfs/zpool.cache \
    -O devices=off \
    -O acltype=posixacl -O xattr=sa \
    -O compression=lz4 \
    -O normalization=formD \
    -O relatime=on \
    -O canmount=off -O mountpoint=/boot -R /mnt \
    bpool ${DISK}-part7

# Not yet
zpool create \
    -o ashift=12 \
    -o autotrim=on \
    -O acltype=posixacl -O xattr=sa -O dnodesize=auto \
    -O compression=lz4 \
    -O normalization=formD \
    -O relatime=on \
    -O canmount=off -O mountpoint=/home -R /mnt \
    hpool ${DISK}-part9

UUID=2204

zfs create -o canmount=off -o mountpoint=none rpool/ROOT
zfs create -o mountpoint=/ rpool/ROOT/ubuntu_$UUID


zfs create -o canmount=off -o mountpoint=none bpool/BOOT
zfs create -o mountpoint=/boot bpool/BOOT/ubuntu_$UUID

zfs create -o canmount=off -o mountpoint=none hpool/USERDATA
zfs create -o mountpoint=/home hpool/USERDATA/ubuntu_$UUID



#Bind the virtual filesystems from the LiveCD environment to the new system and chroot into it:
cd /mnt
mount --make-private --rbind /dev  /mnt/dev
mount --make-private --rbind /proc /mnt/proc
mount --make-private --rbind /sys  /mnt/sys
mount --make-private --rbind /run  /mnt/run
chroot /mnt /usr/bin/env DISK=$DISK UUID=$UUID bash --login
mount -a
 
# You are now in the new system. Your current "/" points to "/rpool/ROOT/ubuntu_$UUID"
# All the following commands will apply only to that system.

## #5
apt update

mkdir /boot/efi
echo /dev/disk/by-uuid/$(blkid -s UUID -o value ${DISK}-part1) \
    /boot/efi vfat defaults 0 0 >> /etc/fstab
mount /boot/efi

mkdir /boot/efi/grub /boot/grub
echo /boot/efi/grub /boot/grub none defaults,bind 0 0 >> /etc/fstab
mount /boot/grub

apt install --reinstall --yes \
    grub-efi-amd64 grub-efi-amd64-signed linux-image-generic \
    shim-signed zfs-initramfs


echo swap ${DISK}-part6 /dev/urandom \
      swap,cipher=aes-xts-plain64:sha256,size=512 >> /etc/crypttab
echo /dev/mapper/swap none swap defaults 0 0 >> /etc/fstab

#swapon -a

#Setup system groups:

Verify that the ZFS boot filesystem is recognized:
grub-probe /boot

#Refresh the initrd files:
update-initramfs -c -k all

#Note: Ignore any error messages saying ERROR: Couldn't resolve device and WARNING: Couldn't determine #root device. cryptsetup does not support ZFS.

#Disable memory zeroing:

vi /etc/default/grub
# Add init_on_alloc=0 to: GRUB_CMDLINE_LINUX_DEFAULT
# Save and quit (or see the next step).

#This is to address performance regressions.

vi /etc/default/grub
# Comment out: GRUB_TIMEOUT_STYLE=hidden
# Set: GRUB_TIMEOUT=5
# Below GRUB_TIMEOUT, add: GRUB_RECORDFAIL_TIMEOUT=5
# Remove quiet and splash from: GRUB_CMDLINE_LINUX_DEFAULT
# Uncomment: GRUB_TERMINAL=console
# Save and quit.

#Later, once the system has rebooted twice and you are sure everything is working, you can undo these #changes, if desired.

#Update the boot configuration:

update-grub


$ update-grub
 
#$ grub-install /dev/sda                # Note: This should be your root disk (not partition!)
grub-install --target=x86_64-efi --efi-directory=/boot/efi \
    --bootloader-id=ubuntu --recheck --no-floppy
 
mkdir /etc/zfs/zfs-list.cache
touch /etc/zfs/zfs-list.cache/bpool
touch /etc/zfs/zfs-list.cache/rpool
zed -F &

#Verify that zed updated the cache by making sure these are not empty:
cat /etc/zfs/zfs-list.cache/bpool
cat /etc/zfs/zfs-list.cache/rpool

#If either is empty, force a cache update and check again:
zfs set canmount=on bpool/BOOT/ubuntu_$UUID
zfs set canmount=on rpool/ROOT/ubuntu_$UUID

#If they are still empty, stop zed (as below), start zed (as above) and try again.
#Once the files have data, stop zed:

fg
#Press Ctrl-C.
sed -Ei "s|/mnt/?|/|" /etc/zfs/zfs-list.cache/*

exit
mount | grep -v zfs | tac | awk '/\/mnt/ {print $3}' | \
    xargs -i{} umount -lf {}
zpool export -a

reboot

## Add kpool
# Type search string, or <Enter> to show all codes: solaris
#
# be00 Solaris boot                        bf00 Solaris root                      
# bf01 Solaris /usr & Mac ZFS              bf02 Solaris swap                      
# bf03 Solaris backup                      bf04 Solaris /var                      
# bf05 Solaris /home                       bf06 Solaris alternate sector          
# bf07 Solaris Reserved 1                  bf08 Solaris Reserved 2                
# bf09 Solaris Reserved 3                  bf0a Solaris Reserved 4                
# bf0b Solaris Reserved 5                  

DISK=/dev/disk/by-id/ata-Samsung_SSD_870_QVO_2TB_S5VWNJ0RA07047N

sgdisk --zap-all $DISK

# For kpool KVM datasets
sgdisk     -n1:0:+1000G   -c1:kpool  -t1:BF07 $DISK

# For dpool data
sgdisk     -n2:0:0       -c2:dpool  -t2:BF07 $DISK

sgdisk -p $DISK
#Disk /dev/disk/by-id/ata-Samsung_SSD_870_QVO_2TB_S5VWNJ0RA07047N: 3907029168 sectors, 1.8 TiB
#Disk identifier (GUID): E379D157-5B27-4A43-8EB1-D41E39668300
#
#Number  Start (sector)    End (sector)  Size       Code  Name
#   1            2048      2097154047   1000.0 GiB  BF07  kpool
#   2      2097154048      3907029134   863.0 GiB   BF07  dpool

mkdir /kpool
mkdir /dpool

zpool create \
    -o ashift=12 \
    -o autotrim=on \
    -o cachefile=/etc/zfs/zpool.cache \
    -O acltype=posixacl -O xattr=sa -O dnodesize=auto \
    -O compression=lz4 \
    -O normalization=formD \
    -O relatime=on \
    -O canmount=off -O mountpoint=/kpool -R /mnt \
    kpool ${DISK}-part1

zpool create \
    -o ashift=12 \
    -o autotrim=on \
    -o cachefile=/etc/zfs/zpool.cache \
    -O acltype=posixacl -O xattr=sa -O dnodesize=auto \
    -O compression=lz4 \
    -O normalization=formD \
    -O relatime=on \
    -O canmount=off -O mountpoint=/dpool -R /mnt \
    dpool ${DISK}-part2

UUID=2204

zfs create -o canmount=off -o mountpoint=none kpool/QEMU-KVM
zfs create -o mountpoint=/kpool kpool/QEMU-KVM/ubuntu_$UUID
mkdir /kpool/ISO
zfs create -o mountpoint=/kpool/ISO kpool/QEMU-KVM/ubuntu_$UUID/ISO
zfs create -o mountpoint=/var/lib/libvirt/images kpool/QEMU-KVM/ubuntu_$UUID/images
zfs create -o mountpoint=/etc/libvirt/ kpool/QEMU-KVM/ubuntu_$UUID/libvirt

rsync -aAXv /etc/libvirt/ /mnt/etc/libvirt
rsync -aAXv /var/lib/libvirt/images/ /mnt/var/lib/libvirt/images
rsync -aAXv /home/mafoelffen/Downloads/ISO/ /mnt/kpool/ISO

# Ensure they are populated
ls /mnt/etc/libvirt/*
ls /mnt/var/lib/libvirt/images/*
ls /mnt/kpool/ISO/*

zfs list
zpool export kpool
zpool import kpool
zfs get mountpoint kpool/QEMU-KVM/ubuntu_$UUID/images
zfs get mountpoint kpool/QEMU-KVM/ubuntu_$UUID/qemu-xml
zfs get mountpoint kpool/QEMU-KVM/ubuntu_$UUID/ISO

zfs create -o canmount=off -o mountpoint=none dpool/DATA
zfs create -o mountpoint=/dpool dpool/DATA/ubuntu_$UUID
zfs list
zpool export dpool
zpool import dpool
zfs get mountpoint dpool

touch /etc/zfs/zfs-list.cache/kpool
touch /etc/zfs/zfs-list.cache/dpool
touch /etc/zfs/zfs-list.cache/hpool

zed -F

#Verify that zed updated the cache by making sure these are not empty:
cat /etc/zfs/zfs-list.cache/bpool
cat /etc/zfs/zfs-list.cache/rpool
cat /etc/zfs/zfs-list.cache/hpool
cat /etc/zfs/zfs-list.cache/kpool
cat /etc/zfs/zfs-list.cache/dpool

#If any is empty, force a cache update and check again:
zfs set canmount=on bpool/BOOT/ubuntu_$UUID
zfs set canmount=on rpool/ROOT/ubuntu_$UUID
zfs set canmount=on bpool/USERDATA/ubuntu_$UUID
zfs set canmount=on kpool/QEMU-KVM/ubuntu_$UUID
zfs set canmount=on dpool/DATA/ubuntu_$UUID

#If they are still empty, stop zed (as below), start zed (as above) and try again.
#Once the files have data, stop zed:

fg
#Press Ctrl-C.
sed -Ei "s|/mnt/?|/|" /etc/zfs/zfs-list.cache/*

exit
mount | grep -v zfs | tac | awk '/\/mnt/ {print $3}' | \
    xargs -i{} umount -lf {}


## Create ZFS Backup pool
# bf03 Solaris backup 
DISK=/dev/disk/by-id/ata-Dogfish_SSD_2TB_AA000000000000001150

sgdisk --zap-all $DISK

# For backup pool for snapshot backup datasets
sgdisk     -n1:0:1500G   -c1:backup  -t1:BF03 $DISK

mkdir /zfs-backups

zpool create \
    -o ashift=12 \
    -o autotrim=on \
    -O acltype=posixacl -O xattr=sa -O dnodesize=auto \
    -O compression=lz4 \
    -O normalization=formD \
    -O relatime=on \
    -O canmount=off -O mountpoint=/zfs-backup \
    backups ${DISK}-part2

UUID=2204

mkdir /zfs-backups/images-vm

zfs create -o canmount=off -o mountpoint=none backups/BACKUPS
zfs create -o mountpoint=/zfs-backups/images-vm backups/BACKUPS/ubuntu_$UUID



# Installed sanoid, and used this command:
syncoid kpool/QEMU-KVM/ubuntu_2204/images backups/BACKUPS/ubuntu_2204/images-vm/2023-07-25

```

---

### Post by MAFoElffen on 2023-11-02
Which turned out like this:
```

NAME                                                                                        USED  AVAIL     REFER  MOUNTPOINT
backups                                                                                     224G  1.20T       96K  /zfs-backups
backups/BACKUPS                                                                             224G  1.20T       96K  none
backups/BACKUPS/ubuntu_2204                                                                 224G  1.20T       96K  /zfs-backups
backups/BACKUPS/ubuntu_2204/images-vm                                                       224G  1.20T       96K  /zfs-backups/images-vm
backups/BACKUPS/ubuntu_2204/images-vm/2023-07-25                                            224G  1.20T      224G  /zfs-backups/images-vm/2023-07-25
bpool                                                                                       709M  1.06G       96K  /boot
bpool/BOOT                                                                                  708M  1.06G       96K  none
bpool/BOOT/ubuntu_2204                                                                      708M  1.06G      708M  /boot
dpool                                                                                      3.05M   829G       96K  /dpool
dpool/DATA                                                                                  192K   829G       96K  none
dpool/DATA/ubuntu_2204                                                                       96K   829G       96K  /dpool
hpool                                                                                      57.2G   326G       96K  /home
hpool/USERDATA                                                                             57.2G   326G       96K  none
hpool/USERDATA/root_2204                                                                   2.86G   326G     2.86G  /root
hpool/USERDATA/ubuntu_2204                                                                 54.3G   326G     54.3G  /home
kpool                                                                                       451G   510G       96K  /kpool
kpool/QEMU-KVM                                                                              451G   510G       96K  none
kpool/QEMU-KVM/ubuntu_2204                                                                  451G   510G       96K  /kpool
kpool/QEMU-KVM/ubuntu_2204/ISO                                                              195G   510G      195G  /home/mafoelffen/Downloads/ISO
kpool/QEMU-KVM/ubuntu_2204/images                                                           256G   510G      239G  /var/lib/libvirt/images
kpool/QEMU-KVM/ubuntu_2204/libvirt                                                          536K   510G      536K  /etc/libvirt/
rpool                                                                                      23.7G   457G       96K  /
rpool/ROOT                                                                                 23.7G   457G       96K  none
rpool/ROOT/ubuntu_2204                                                                     23.7G   457G     8.74G  /
rpool/ROOT/ubuntu_2204/srv                                                                   96K   457G       96K  /srv
rpool/ROOT/ubuntu_2204/tmp                                                                  244K   457G      244K  /tmp
rpool/ROOT/ubuntu_2204/usr                                                                 3.32G   457G       96K  /usr
rpool/ROOT/ubuntu_2204/usr/local                                                           3.32G   457G     3.32G  /usr/local
rpool/ROOT/ubuntu_2204/var                                                                 11.6G   457G       96K  /var
rpool/ROOT/ubuntu_2204/var/cache                                                            614M   457G      614M  /var/cache
rpool/ROOT/ubuntu_2204/var/games                                                             96K   457G       96K  /var/games
rpool/ROOT/ubuntu_2204/var/lib                                                             6.35G   457G     6.18G  /var/lib
rpool/ROOT/ubuntu_2204/var/lib/AccountsService                                              112K   457G      112K  /var/lib/AccountsService
rpool/ROOT/ubuntu_2204/var/lib/NetworkManager                                               444K   457G      444K  /var/lib/NetworkManager
rpool/ROOT/ubuntu_2204/var/lib/apt                                                          104M   457G      104M  /var/lib/apt
rpool/ROOT/ubuntu_2204/var/lib/docker                                                        96K   457G       96K  /var/lib/docker
rpool/ROOT/ubuntu_2204/var/lib/dpkg                                                        62.1M   457G     62.1M  /var/lib/dpkg
rpool/ROOT/ubuntu_2204/var/lib/nfs                                                          104K   457G      104K  /var/lib/nfs
rpool/ROOT/ubuntu_2204/var/log                                                              650M   457G      650M  /var/log
rpool/ROOT/ubuntu_2204/var/mail                                                              96K   457G       96K  /var/mail
rpool/ROOT/ubuntu_2204/var/snap                                                            3.59G   457G     3.59G  /var/snap
rpool/ROOT/ubuntu_2204/var/spool                                                            336K   457G      336K  /var/spool
rpool/ROOT/ubuntu_2204/var/tmp                                                              452M   457G      452M  /var/tmp
rpool/ROOT/ubuntu_2204/var/www                                                               96K   457G       96K  /var/www

```

---

### Post by aljames2 on 2023-11-02
I see, so we need to create these mountpoints (and others) ahead of time , and KVM will install into the pool.  That was my conflict, I was thinking I  might should (bad grammer), install KVM first to create these locations but I see now it wouldn't be installed in the pool.

```

mkdir /etc/libvirt
mkdir /var/lib/libvirt

```

I am also creating snpool, to also be on a separate disk to send my snapshots to, vs. having them in the root spaces.

I don't see snapshots as a backup thought, while it may actually be in the ZFS world, I still prefer to pull backups from these snapshots.  For that I think I will go back to using LVM on the backup server and pull from these ZFS pools my backups using rdiff-backup.

I suppose EXT4+LVM backups can be rsync'd into ZFS pools for later if needed, while preserving ownerships and such.

---

### Post by MAFoElffen on 2023-11-02
Snapshots create as a dataset in a pool, which you can then send/receive to other pools. That is how I do that to get my snapshots to my backups pool. As long as you create that snapshot with the "current data", versus, changes just tracking changes from that point... then you can delete the snapshot in that original pool... To send/receive it back to restore it.

What makes a backup a backup , when you can store a copy of the data "somewhere else", and bring it back to restored it.

rsync just works... but it doesn't care about anything except files written onto a filesystem. It really doesn't deal with the filesystem or volume manager that filesystem resides in. It does carry over the ownership and permissions of the files with them.

---

### Post by aljames2 on 2023-11-03
Thank you MAFoElffen!

I think I am straight and back on track now. My steps are very similar to yours with some variations. I used the OpenZFS setup instructions to get started but wanted to integrate some other pools and their instructions were lacking in this respect.

I think I'm ready to tear down my draft setup now and rebuild it to make sure I can replicate.  Then I'll start adding some VMs and get on with some in-home production stuff.

I'm rolling with Ubuntu 22.04 figuring I have until spring 2027 before needing to rebuild.  My guess is an upgrade will break things at that time, but 3 more years until then is do'able.

---

