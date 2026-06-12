---
title: "So, Ubuntu 23.10 is bringing back zfs in installer..."
date: 2023-10-03
forum: Installation &amp; Upgrades
---

### Post by laserburn2 on 2023-10-03
I'm using 22.04.3 with zfs and I've had a myriad problems because of it. Mind you, not with zfs itself, that was working well, but with the fact that the Ubuntu installer created a 2GB bpool for /boot, which seemed plenty, but trust me, it isn't.  

Tired of dealing with the system problems, I'll probably install Ubuntu 23.10 when it comes out. I thought that would be the end of zfs for me, but then I thought maybe they have actually made installer smarter this time, maybe it now makes a larger bpool or lets the user decide bpool size. Does anyone have any info on this?

---

### Post by #&amp;thj^% on 2023-10-03
> **laserburn2 said:**
> I'm using 22.04.3 with zfs and I've had a myriad problems because of it. Mind you, not with zfs itself, that was working well, but with the fact that the Ubuntu installer created a 2GB bpool for /boot, which seemed plenty, but trust me, it isn't.  

Goodness it's been plenty for me from 20.04 to 23.10
```
zpool list
NAME    SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
bpool  1.88G   126M  1.75G        -         -     0%     6%  1.00x    ONLINE  -
rpool   232G  18.7G   213G        -         -     4%     8%  1.00x    ONLINE  -


```
Maybe some understanding might help, I remember you having problems with system snapshots a while back.
But I've not had a single issue with a 2Gig bpool.
Why would you need more?

---

### Post by MAFoElffen on 2023-10-03
I traced through your saga. As I said in your "Round 2" thread...The only reason you are going to need more than 2GB in bpool (a separate boot partition) is if you didn't pay attention:
> **MAFoElffen said:**
> 
The canned install script for that sets  the partition for bpool which mounts at boot, at 2GB. Larger than any  other install script... You just need to do maintenance, delete the old  snapshots, and set the conf file for automatic snapshots at 10 or less.  Default for that is 20.

22.04 and on didn't install, nor use zsys anymore. That is where "you said" you had troubles in your very first thread... 

Did you have it present? Do you actually have the zsys services there and enabled?

If so, 

[LIST=1]
[*]Did you follow my instructions to limit the zsys triggered snapshots to around 5 snap shots??? That would limit the snapshot count to 5, instead of the default 20. 
[*]If you have it and didn't do that, then why have you not disabled and masked the services... then uninstalled the zsys package? That would turn off the automatic snapshots 
[/LIST]
 
I think we gave you those recommendations in your last thread back in July, right? It is now October.

I am testing the ZFS canned installer scripts in 23.10. And it is installing just fine, with 2GB bpool, and no 'zsys' package... So it does not fill up the pool with snapshots of bpool.

EDIT:
I may be confused. In your first thread, and into your second thread, you had zsys enabled... Which meant you must have installed ZFS with the 20.04 LTS installer. Becasue even though by the second thread, that you said had 22.04 installed, but that pacakge was not installed by default in the 22.04 installer. The point I'm bringing up it that both those were LTS releases... Why would you now install an interim release (23.10), when 24.04 LTS is just 6 months down the road?

---

### Post by laserburn2 on 2023-10-04
Uff, it's a long story that I really don't feel like getting into. I started with 20.04, everything was super until 22.04 upgrade, then the space starts running out. Because currently I have kernel 6.2 and also 5.11 and also whatever was before that, all those branches have two latest kernels, plus nvidia graphic drivers take a load of space, plus linux firmware, it's a total mess. Whenever something needs to be updated on bpool, I first have to make space by removing snapshots and if it's a lot of packages at once, that might not even be enough. I just don't have it in me to fight with this any more. 

And all I need is just to make bpool a bit bigger, so that with passage of time I wouldn't run into this same problem again, disk space is plentiful. But apparently, it is fixed size, Canonical won't let users make any changes to zfs pools during the installation.

---

### Post by MAFoElffen on 2023-10-04
If you are planning on doing a fresh install... Then you can choose any size you want for your targets, if installed manually. 

If installed with the canned default scripts. I'm sure there is a way, somewhere, to pop out to a command line prompt and change "some" variable "somewhere" to change that. I'm honestly not sure what variable at where. But I know with adding custom LUKS's layout to installers, that "that" posibility exists.

That is a very good question, and you have peaked my curiosity enough to ask the developers at GitHub. I will ask, play with that and document if that is possible. That could work to choose custom sizes for EFI and Boot. Hmmm.

But you need to understand, that, just because it something "is possible" doesn't meant it's a good idea to do things that way. LOL That would still be an advanced method, outside the box.

---

### Post by laserburn2 on 2023-10-04
Installer back in the days did not allow any manual configuration if you wanted zfs, you could only let the installer autoconfigure the filesystem and that was it. I'm not unhappy with zfs or zsys, my problems all came out of too small bpool. I believe there is no good reason to not allow users to have a larger bpool, it's probably just one variable after all.

---

### Post by MAFoElffen on 2023-10-04
When I said 'manually'... That's what I meant. I type out my plan and all the commands I will use in a text document. Then I boot from an Installer disk with a live environemnt. For me, that doesn't matter which installer, because I'm not using the installer itself at all. I'm using a terminal session to install opnessh-server.

Then I start a graphical terminal session on my laptop or workstation. I sue that plan to copy and paste my commands in, an copy the output I need to alter the commands from what I get from that. Later, that plan is my record of how that machine is installed. 

Here is the one from my workstation. Notice that I set my bpool / boot partition at 3GB:
```

## Migration for my MSI MPG Workstation from an old SuperMicro Server board

ssh root@10.0.0.141 

sudo su -

apt install zfs-dkms zfs-initramfs

ls -la /dev/disk/by-id

DISK=/dev/disk/by-id/nvme-Samsung_SSD_990_PRO_2TB_S73WNJ0W310240K
DISK2=/dev/disk/by-id/nvme-PCIe_SSD_23011650000181
DISK3=/dev/disk/by-id/nvme-PCIe_SSD_23011650000183

sgdisk --zap-all $DISK2
sgdisk --zap-all $DISK3

gdisk $DISK

## Recipe details
# Name                  Layout    Code  Type              
#  |_ boot_grub         1:+750M   EF00  ESP
##
#  |_ Swap              0:+3G     BF02  Solaris Swap
#  |_ rpool/ROOT        0:+5G     BFOO  Solaris Root
#  |_ homepool/USERDATA 0:0       BFO5  Solaris Home

## Existing
#Number  Start (sector)    End (sector)  Size       Code  Name
#   1            2048         1128447   750.0 MiB   EF00  EFI
#   2         1128448         1390591   128.0 MiB   0C01  Mi
#   3         1390592      1888827391   900.0 GiB   0700  WIN10
#   4      3842101248      3844114431   983.0 MiB   2700  
#   5      3844114432      3907028991   30.0 GiB    2700  

ls -lah /dev/disk/by-id/
DISK=/dev/disk/by-id/ata-Samsung_SSD_870_QVO_2TB_S6R4NJ0R624350W

## Add partitions
# For ESP EFI
sgdisk     -n1:0:+750M   -c1:EFI    -t1:EF00 $DISK

# For bpool boot
[COLOR=#ff0000]sgdisk     -n2:0:+3G     -c2:bpool  -t2:BE00 $DISK[/COLOR]

# For rpool root
sgdisk     -n3:0:+750G   -c3:rpool  -t3:BF00 $DISK

# For Linux Swap
sgdisk     -n4:0:+250G   -c4:swap   -t4:BF02 $DISK

# For hpool home
sgdisk     -n5:0:359G    -c5:hpool  -t5:BF05 $DISK

# For kpool KVM
sgdisk     -n6:0:465G    -c6:kpool  -t6:BF07 $DISK
sgdisk     -n1:0:465G    -c1:kpool  -t1:BF07 $DISK2
#sgdisk     -n1:0:465G    -c1:kpool  -t1:BF07 $DISK3

# DISK
#Number  Start (sector)    End (sector)  Size       Code  Name
#   1            2048         1538047   750.0 MiB   EF00  EFI
#   2         1538048         7829503   3.0 GiB     BE00  bpool
#   3         7829504      1580693503   750.0 GiB   BF00  rpool
#   4      1580693504      2104981503   250.0 GiB   BF02  swap
#   5      2104981504      2857859071   359.0 GiB   BF05  Solaris /home
#   6      2857859072      3833034751   465.0 GiB   BF07  kpool
#
#nvme0n1                         1.8T             
#&#9500;&#9472;nvme0n1p1                     750M             
#&#9500;&#9472;nvme0n1p2                       3G             
#&#9500;&#9472;nvme0n1p3                     750G             
#&#9500;&#9472;nvme0n1p4                     250G             
#&#9500;&#9472;nvme0n1p5                     359G             
#&#9492;&#9472;nvme0n1p6                     465G             
#
## DISK2
#Number  Start (sector)    End (sector)  Size       Code  Name
#   1            2048       975177727   465.0 GiB   BF07  kpool
#
#nvme1n1                       465.8G             
#Number  Start (sector)    End (sector)  Size       Code  Name
#   1            2048       975177727   465.0 GiB   BF07  kpool
#&#9492;&#9472;nvme1n1p1                     465G             
#
## Disk3 Undecided yet
#nvme2n1                       465.8G             
#&#9492;&#9472;nvme2n1p1                     465G             
#

zpool create \
    -o ashift=13 \
    -o autotrim=on \
    -O acltype=posixacl -O xattr=sa -O dnodesize=auto \
    -O compression=lz4 \
    -O normalization=formD \
    -O relatime=on \
    -O canmount=off -O mountpoint=/ -R /mnt \
    rpool $DISK-part3

zpool create \
    -o ashift=13 \
    -o autotrim=on \
    -o cachefile=/etc/zfs/zpool.cache \
    -O devices=off \
    -O acltype=posixacl -O xattr=sa \
    -O compression=lz4 \
    -O normalization=formD \
    -O relatime=on \
    -O canmount=off -O mountpoint=/boot -R /mnt \
    bpool ${DISK}-part2

# Not yet
zpool create \
    -o ashift=13 \
    -o autotrim=on \
    -O acltype=posixacl -O xattr=sa -O dnodesize=auto \
    -O compression=lz4 \
    -O normalization=formD \
    -O relatime=on \
    -O canmount=off -O mountpoint=/home -R /mnt \
    hpool ${DISK}-part5

UUID=2204

zfs create -o canmount=off -o mountpoint=none rpool/ROOT
zfs create -o mountpoint=/ rpool/ROOT/ubuntu_$UUID

zfs create -o canmount=off -o mountpoint=none bpool/BOOT
zfs create -o mountpoint=/boot bpool/BOOT/ubuntu_$UUID

zfs create -o canmount=off -o mountpoint=none hpool/USERDATA
zfs create -o mountpoint=/home hpool/USERDATA/ubuntu_$UUID

zfs create -o canmount=off \
    rpool/ROOT/ubuntu_$UUID/usr
zfs create -o canmount=off \
    rpool/ROOT/ubuntu_$UUID/var
zfs create rpool/ROOT/ubuntu_$UUID/var/lib
zfs create rpool/ROOT/ubuntu_$UUID/var/log
zfs create rpool/ROOT/ubuntu_$UUID/var/spool
zfs create rpool/USERDATA
zfs create -o canmount=on \
    -o mountpoint=/root \
    rpool/USERDATA/root_$UUID
chmod 700 /mnt/root

zfs create rpool/ROOT/ubuntu_$UUID/var/cache
zfs create rpool/ROOT/ubuntu_$UUID/var/lib/nfs
zfs create rpool/ROOT/ubuntu_$UUID/var/tmp
chmod 1777 /mnt/var/tmp

zfs create rpool/ROOT/ubuntu_$UUID/var/lib/apt
zfs create rpool/ROOT/ubuntu_$UUID/var/lib/dpkg
zfs create rpool/ROOT/ubuntu_$UUID/srv
zfs create rpool/ROOT/ubuntu_$UUID/usr/local
zfs create rpool/ROOT/ubuntu_$UUID/var/games
zfs create rpool/ROOT/ubuntu_$UUID/var/lib/AccountsService
zfs create rpool/ROOT/ubuntu_$UUID/var/lib/NetworkManager
zfs create rpool/ROOT/ubuntu_$UUID/var/lib/docker
zfs create rpool/ROOT/ubuntu_$UUID/var/mail
zfs create rpool/ROOT/ubuntu_$UUID/var/snap
zfs create rpool/ROOT/ubuntu_$UUID/var/www

######
# Copy in the existing filesystem
######
# Mount the old drive into /media/mafoelffen/
# The old was LVM2 vg0-lv--0 on /dev/sdb5...
vgchange -a y
lvscan
# 1 logical volume(s) in volume group "vg0" now active
ls /dev/mapper
#control  vg0-lv--0
lvscan
#  ACTIVE            '/dev/vg0/lv-0' [<100.00 GiB] inherit
mkdir /data
mount /dev/vg0/lv-0 /data
# rsync the filesystem into the new structure
rsync -aAXv --one-file-system /data/ /mnt
######
mkdir /mnt/etc/zfs
cp /etc/zfs/zpool.cache /mnt/etc/zfs/



#Bind the virtual filesystems from the LiveCD environment to the new system and (later) chroot into it:
cd /mnt
mount --make-private --rbind /dev  /mnt/dev
mount --make-private --rbind /proc /mnt/proc
mount --make-private --rbind /sys  /mnt/sys
mount --make-private --rbind /run  /mnt/run
chroot /mnt /usr/bin/env DISK=$DISK UUID=$UUID bash --login
#mount -a

# You are now in the new system. Your current "/" points to "/rpool/ROOT/ubuntu_$UUID"
# All the following commands will apply only to that system.

apt update

apt install --yes dosfstools

mkdosfs -F 32 -s 1 -n EFI ${DISK}-part1

mkdir /boot/efi
echo /dev/disk/by-uuid/$(blkid -s UUID -o value ${DISK}-part1) \
    /boot/efi vfat defaults 0 0 >> /etc/fstab
mount /boot/efi

mkdir /boot/efi/grub /boot/grub
echo /boot/efi/grub /boot/grub none defaults,bind 0 0 >> /etc/fstab
mount /boot/grub

apt install --reinstall --yes \
    grub-efi-amd64 grub-efi-amd64-signed linux-image-generic \
    shim-signed zfs-initramfs zfsutils-linux

mkswap -f ${DISK}-part4
echo /dev/disk/by-uuid/$(blkid -s UUID -o value ${DISK}-part4) \
    none swap discard 0 0 >> /etc/fstab
swapon -a

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
 
#$ grub-install /dev/sda                
# Note: This should be your root disk (not partition!)

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

## Notes: On export, pools were busy. On reboot, had to force import rpool, then
zfs mount -a... Then import hpool. Then update-initramfs.

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

DISK=/dev/disk/by-id/nvme-Samsung_SSD_990_PRO_2TB_S73WNJ0W310240K
DISK2=/dev/disk/by-id/nvme-PCIe_SSD_23011650000181
DISK3=/dev/disk/by-id/nvme-PCIe_SSD_23011650000183

sgdisk -p $DISK
#Disk /dev/disk/by-id/nvme-Samsung_SSD_990_PRO_2TB_S73WNJ0W310240K: 3907029168 sectors, 1.8 TiB
#Number  Start (sector)    End (sector)  Size       Code  Name
#   1            2048         1538047   750.0 MiB   EF00  EFI
#   2         1538048         7829503   3.0 GiB     BE00  bpool
#   3         7829504      1580693503   750.0 GiB   BF00  rpool
#   4      1580693504      2104981503   250.0 GiB   BF02  swap
#   5      2104981504      2857859071   359.0 GiB   BF05  Solaris /home
#   6      2857859072      3833034751   465.0 GiB   BF07  kpool

sgdisk -p $DISK2
#Disk /dev/disk/by-id/nvme-PCIe_SSD_23011650000181: 976773168 sectors, 465.8 GiB
#Number  Start (sector)    End (sector)  Size       Code  Name
#   1            2048       975177727   465.0 GiB   BF07  kpool

sgdisk -p $DISK3
#Disk /dev/disk/by-id/nvme-PCIe_SSD_23011650000183: 976773168 sectors, 465.8 GiB
#Number  Start (sector)    End (sector)  Size       Code  Name
#   1            2048       975177727   465.0 GiB   BF07  kpool

## kpool is going to be on partition 6 of DISK-part6, and later add DISK2-part1

mkdir /kpool
mkdir /kpool/ISO
mkdir /kpool/KVM-VM

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
    kpool ${DISK}-part6


zpool add kpool $DISK2-part1

UUID=2204

zfs create -o canmount=off -o mountpoint=none kpool/QEMU-KVM
zfs create -o mountpoint=/kpool kpool/QEMU-KVM/ubuntu_$UUID
zfs create -o mountpoint=/kpool/ISO kpool/QEMU-KVM/ubuntu_$UUID/ISO
zfs create -o mountpoint=/kpool/KVM-VM kpool/QEMU-KVM/ubuntu_$UUID/KVM-VM
zfs create -o mountpoint=/var/lib/libvirt/images kpool/QEMU-KVM/ubuntu_$UUID/images
zfs create -o mountpoint=/etc/libvirt/ kpool/QEMU-KVM/ubuntu_$UUID/libvirt

# Get ISO'es from main KVM server
#scp mafoelffen@10.0.0.3:/data/ISO/* /mnt/kpool/ISO/
rsync -aAXv mafoelffen@10.0.0.3:/data/ISO/ /mnt/kpool/ISO
rsync -aAXv /etc/libvirt/ /mnt/etc/libvirt
rsync -aAXv /var/lib/libvirt/images/ /mnt/var/lib/libvirt/images
#rsync -aAXv /home/mafoelffen/Downloads/ISO/ /mnt/kpool/ISO

# Ensure they are populated
ls /mnt/etc/libvirt/*
ls /mnt/var/lib/libvirt/images/*
ls /mnt/kpool/ISO/*

rm -R /etc/libvirt/*
rm -R /var/lib/libvirt/images/*


zfs list
zpool export kpool
zpool import kpool
zfs get mountpoint kpool/QEMU-KVM/ubuntu_$UUID/images
zfs get mountpoint kpool/QEMU-KVM/ubuntu_$UUID/libvirt
zfs get mountpoint kpool/QEMU-KVM/ubuntu_$UUID/ISO

zfs list

## DPOOL
zpool create \
    -o ashift=12 \
    -o autotrim=on \
    -O acltype=posixacl -O xattr=sa -O dnodesize=auto \
    -O compression=lz4 \
    -O normalization=formD \
    -O relatime=on \
    -O canmount=off -O mountpoint=/dpool -R /mnt \
    dpool ${DISK3}-part1

UUID=2204

zfs create -o canmount=off -o mountpoint=none dpool/DATA
zfs create -o mountpoint=/dpool dpool/DATA/ubuntu_$UUID
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

######### Stopped here for now ##################
## Create ZFS 8TB storage pool
# bf03 Solaris storage pool 
DISK=/dev/disk/by-id/scsi-SJMicron__201704214175

sgdisk --zap-all $DISK

# For storage pool for media and backup datasets
sgdisk     -n1:0:0  -c1:mpool  -t1:BF03 $DISK

mkdir /mpoolEcho $DISK

zpool create \
    -o ashift=12 \
    -o autotrim=on \
    -O acltype=posixacl -O xattr=sa -O dnodesize=auto \
    -O compression=lz4 \
    -O normalization=formD \
    -O relatime=on \
    -O canmount=off -O mountpoint=/mpool \
    mpool ${DISK}-part1

UUID=2204

mkdir /mpool/media
mkdir /mpool/backups

zfs create -o canmount=off -o mountpoint=none mpool/BACKUPS
zfs create -o mountpoint=/mpool/backups mpool/BACKUPS/ubuntu_$UUID
zfs create -o canmount=off -o mountpoint=none mpool/MEDIA
zfs create -o mountpoint=/mpool/media mpool/MEDIA/ubuntu_$UUID

### Make copy of old SSD for migration
# Old Windows install was MBR...
mkdir /mpool/backups/SSD-500-01

DISK1=/dev/disk/by-id/scsi-SATA_Samsung_SSD_870_S62ANJ0R237769K
sudo dd if=${DISK1} of=/mpool/backups/SSD-500-01/ssd500-full.img bs=64k staus=progress
sudo dd if=${DISK1}-part1 of=/mpool/backups/SSD-500-01/ssd500-part1.img bs=64k status=progress
sudo dd if=${DISK1}-part2 of=/mpool/backups/SSD-500-01/ssd500-part2.img bs=64k  status=progress
sudo dd if=${DISK1}-part3 of=/mpool/backups/SSD-500-01/ssd500-part3.img bs=64k  status=progress
sudo dd if=${DISK1}-part4 of=/mpool/backups/SSD-500-01/ssd500-part4.img bs=64k  status=progress
sudo dd if=${DISK1}-part5 of=/mpool/backups/SSD-500-01/ssd500-part5.img bs=64k  status=progress

### Switch out one the 500GB kpool NVMe SSD which 1TB of the second 990 Pro NVMe...
DISK1=/dev/disk/by-id/nvme-PCIe_SSD_23011650000181 # in kpool now
DISK2=/dev/disk/by-id/nvme-Samsung_SSD_990_PRO_2TB_S73WNJ0W618194B

sgdisk     -n1:0:1T    -c1:kpool  -t1:BF07 $DISK2
zpool replace kpool $DISK1-part1 $DISK2-part1


# Prep DISK1 for Windows install (Give it something to find easily)
sgdisk --zap-all $DISK1
sgdisk     -n1:0:0    -c1:install_here  -t1:0700 $DISK1

### Other
# Installed sanoid, and used this command:
syncoid kpool/QEMU-KVM/ubuntu_2204/images backups/BACKUPS/ubuntu_2204/images-vm/2023-07-25

```
There are many ways to install Linux.

---

### Post by laserburn2 on 2023-10-05
I'm not that king of a masochist. I'd prefer if I could change a number in some config file on the iso, that would be lovely. Option to choose during the installation would obviously be the best, but beggars can't be choosers.

---

### Post by MAFoElffen on 2023-10-06
You, as a user, could suggest that as an improvement to the installer at Launchpad.net, as a "question"... Or at GitHub: [ubuntu-desktop-installer, Issues]("https://github.com/canonical/ubuntu-desktop-installer/issues"). They are the maintainers of the new installer.

---

### Post by MAFoElffen on 2023-10-06
I asked at the Canonical 'ubuntu-desktop-installer' GitHub as a feature/improvement question: [https://github.com/canonical/ubuntu-desktop-installer/issues/2361](https://github.com/canonical/ubuntu-desktop-installer/issues/2361)

I also asked at Launchpad: [https://answers.launchpad.net/ubuntu/+question/708132](https://answers.launchpad.net/ubuntu/+question/708132)

---

### Post by laserburn2 on 2023-10-07
Thanks, though I doubt it would do much good. If we're very lucky, it might arrive in time for 24.04.

---

### Post by MAFoElffen on 2023-10-07
> **laserburn2 said:**
> Thanks, though I doubt it would do much good. If we're very lucky, it might arrive in time for 24.04.
LMAO! 

Maybe. I figured I would try the normal channels, before I start emailing people directly to bug them. But I like to try to stay in their good graces.

---

### Post by laserburn2 on 2023-10-21
As I expected, no answer. My system miraculously managed to survive a slew of kernel and driver updates and if it breaks, I got a USB stick with Ubuntu 23.10 MM waiting. Situation is not bad, but I hope that we end up with with this option, if not now, than at least when new LTS comes in the spring. As it is right now, if you want to use zfs, do not upgrade your LTS, install fresh, you'll thank me later.

---

### Post by MAFoElffen on 2023-10-21
I'm not giving up. I want "things" to be able to do what I can do with that. I still need answers.

Most of what I've found out for other things with, the new installer, I've had to trace through the system while it's installing and read through their Code to try to find things.

It shouldn't be this hard to get answers from them about this. No one wants to talk about it... It isn't like I am asking them to do something that would cause them any work on their part. Can you hear my frustration coming through the page with this?

Dang. Going to try to pull some favors.

---

