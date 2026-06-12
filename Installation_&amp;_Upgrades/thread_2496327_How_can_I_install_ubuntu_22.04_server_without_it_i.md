---
title: "How can I install ubuntu 22.04 server without it installing grub?"
date: 2024-03-24
forum: Installation &amp; Upgrades
---

### Post by bbergquist0930 on 2024-03-24
I have an already partitioned disk with grub installed and I manage the grub configuration myself to ensure it does exactly what I want.  I want to install Ubuntu server 22.04 onto an empty partition but I don't want it to install grub and wreck my carefully crafted grub configuration.  I will manually update the configuration to allow the installed Ubuntu 22.04 server to boot.

I cannot find an option to not install grub!

Any help will be greatly appreciated.

---

### Post by yancek on 2024-03-24
I don't see any option in the tutorial at the Ubuntu site (linked below) and have never installed the server myself.  Seems a bit odd to me as almost any Linux I have installed with Grub gives options.  Is your current install UEFI or Legacy?  Which server version are you using?  The installer may overwrite the EFI files for your current Ubuntu so I would copy those to a location other than EFI so you can copy them back if necessary.  If you install the server and reboot, verify what is booting so that if you are booting into the server version, check to see if there is an entry for your other Linux and you can boot it and install Grub from that system.  If the other Linux does not show, you should boot into the server version and verify that os-prober is enabled and run update-grub to get an entry for the previous Linux system to boot it an reinstall Grub.  It's surprising to me that there is no option with Grub.  Other possibilities would be installing ubuntu server in virtual software or to a separate physical drive.   

[https://ubuntu.com/tutorials/install-ubuntu-server#1-overview](https://ubuntu.com/tutorials/install-ubuntu-server#1-overview)

---

### Post by aljames2 on 2024-03-24
Is this a dual boot environment, if so wait for other help. I don’t have any experience with dual boot.

My next thought is whether you have good a backup of your grub configuration to where you could allow a normal installation & then bring those changes over from your backups. Not sure if you have rewritten some of your grub code or just made changes in the /etc/default/grub file.

---

### Post by oldfred on 2024-03-24
UEFI or BIOS system?

Have not installed server for years and then just as a test.
But there was this option from terminal.
sudo ubiquity -b

But server now uses subiquity installer, do not know if -b option still available.

If UEFI, you could create a tiny ESP with boot,esp flags and install to that.
Then move flags back to your ESP, & delete extra entry in UEFI boot menu.

With my desktop installs I always turn os-prober off and add my own boot stanza into 40_custom for all the other installs I may want to boot. The os-prober scan looks at too many partitions & finds some obsolete installs I do not want in grub meny anyway.
I use UEFI and install grub to sdb drive, or manually edit /efi/EFI/ubuntu/grub.cfg with UUID of main working install when new install overwrites it.

---

### Post by mikechant on 2024-03-24
I haven't tried it, but [this post]("https://askubuntu.com/questions/1382898/installing-20-04-3-server-subiquity-without-grub") says you may be able to specify
```
subiquity --bootloader=none
```

I'm a "no bootloader" type myself, I've used "ubiquity -b" and, with the Calamares installer, just not specified an ESP/EFI partition (which also worked fine), but I haven't needed to use subiquity yet so I don't know if this flag still works. Hopefully subiquity will reject it rather than ignore it if it's not supported.

---

### Post by MAFoElffen on 2024-03-24
You can also boot from any installer LiveUSB and use 'debootstrap' (after that package is installed by you)... which will install the Ubuntu base core system. Then chroot into the installed system to configure it. Then install package 'ubuntu-server'. there is also package 'ubuntu-server-minimal' if you want to keep out the fluff.

I do this method of installation very often, for many variations of custom installs. That way I have total control of what is installed and how.

I think it is a worthwhile skill to learn.

---

### Post by bbergquist0930 on 2024-03-24
Thanks for all of the help. 

The actual target is old BIOS as it is old hardware but I am familiar with UEFI and the ESP partition.  

I do think the `debootsrap` method will likely be the method that I end up with.   I am actually looking to install RAUC as well and have a system that I can update atomically and the `debootstrap` method may be the cleanest

I am going to give it a try.

---

### Post by bbergquist0930 on 2024-03-24
What about using the Cubic system here to customize the ISO?

---

### Post by MAFoElffen on 2024-03-24
You want help with a debootstrap recipe? Search my name on the forum. I've posted a few that you could modify to your needs.

Or here is one with all my notes, to modify from for LUKS-LVM.... I create a recipe. Add all the commends I'll need. Modify the DISK variable to what comes up... Basically, I create a plan. From a Server Edition LiveUSB, go past the Language and Keyboard panels > Help, Select command line > install openssh-server > connect to it from my workstation, from a graphical terminal session. That way I can cut-and-paste my commands. Then on any output, cut-and-paste into my recipe, to change the variables, and to document what happened in the install. That way, I have a record.:
```

### Encrypted LUKS with LVM2

# Become root
sudo su

# Create an alias variable, as a shortcut to typing it out each time
DISK=$(ls -l /dev/disk/by-id | awk '/sda/ {print "/dev/disk/by-id/"$9}' | head -n 1 )
echo -e "Disk found: $DISK"

# This is a USB for my keyfile
DEST=/dev/sdb1/luks.key
openssl genrsa -out /mnt/luks.key 4096
chmod -v 0400 $DEST
chown root:root $DEST

#Note that this is a specific disk identifier

# Partition the disk 
sgdisk  -n1:1M:+750M -t1:EF00 -c1:EFI  $DISK  # Create EFI partition
sgdisk  -n2:0:+6G    -t2:8200 -c2:SWAP $DISK  # Create Swap partition
sgdisk  -n3:0:+2G    -t3:8309 -c3:BOOT $DISK  # Create Boot partition
sgdisk  -n4:0:+25G   -t4:8309 -c4:ROOT $DISK  # Create Root partition
sgdisk  -n5:0:0      -t4:8309 -c5:HOME $DISK  # Create Home partition

# Display partition table
sgdisk -p $DISK

# Format EFI partition
mkfs.vfat -F 32 -s 1 -n EFI ${DISK}-part1

# Format Boot as LUKS1 in a LUKS1 container
cryptsetup luksFormat --type luks1 -c aes-xts-plain64 -s 512 -h sha256 ${DISK}-part3

cryptsetup luksAddKey ${DISK}-part3 $DEST

ls /dev/mapper/

cryptsetup luksOpen ${DISK}-part3 luks1
mkfs.ext4 -L BOOT /dev/mapper/luks1


# mount /dev/mapper/luks1 /boot

# Create LUKS2 container and format for ROOT
cryptsetup luksFormat --type luks2 -c aes-xts-plain64 -s 512 -h sha256 ${DISK}-part4

cryptsetup luksAddKey ${DISK}-part4 $DEST

cryptsetup luksOpen ${DISK}-part4 luks2

# Create LUKS2 container and format for HOME
cryptsetup luksFormat --type luks2 -c aes-xts-plain64 -s 512 -h sha256 ${DISK}-part5

cryptsetup luksAddKey ${DISK}-part5 $DEST

cryptsetup luksOpen ${DISK}-part5 luks3

# Create encrypted Swap later in fstab using cryptab

# Verify that keys are set in the keslots

# Create LVM2
pvcreate /dev/mapper/luks[2,3] ${DISK}-part2luks

vgcreate vg_root /dev/mapper/luks2
vgcreate vg_home /dev/mapper/luks3
vgcreate vg_swap ${DISK}-part2

lvcreate -l 80%FREE -n lv_root vg_root
lvcreate -l 80%FREE -n lv_home vg_home
lvcreate -l 100%FREE -n lv_swap vg_swap 

### 
Leave the terminal session open...

Start up installer. When it gets to the partition stage, choose "Something else"...

Select sda1. Change. Format. Use as EFI filesystem.

Select /dev/mapper/luks1 (Linux device-mapper (crypt)). Change. Use as ext4, format, /boot.

Select /dev/mapper/vg_root-lv_root (Linux device-mapper (crypt)). Change. Use as ext4, format, /.

Select /dev/mapper/vg_home-lv_home. Change. Use as ext4, format, /home.

Select /dev/mapper/vg_swap-lv_swap. Change

Continue Install. At completion, DO NOT REBOOT. Instead choose "Continue Testing".

Go back to the open terminal session, which you are still root...
###
mkdir -p /target
MapMount=$(ls /dev/mapper/vg_root-lv_root)
mount $MapMount /target
for DIR in proc sys dev /etc/resolv.conf; do mount --rbind /$DIR /target/$DIR; done
mount -a

blkid | grep 'sda' | grep -e 'crypto_LUKS\|SWAP' | awk '{print $1 " " $2 " " $4}'
# copy that output to an editor...

###
SAMPLE:
root@ubuntu:/# blkid | grep 'sda' | grep -e 'crypto_LUKS\|SWAP' | awk '{print $1 " " $2 " " $4}'
/dev/sda4: UUID="bc0c4867-6a91-4f2d-a257-4374d3b8a83c" PARTLABEL="ROOT"
/dev/sda2: UUID="eHwceL-GwKl-TQuK-2Ddh-zElM-EDn5-iOLvMn" PARTLABEL="SWAP"
/dev/sda5: UUID="1d1eaa5a-3d67-4568-b4d8-c15a87c7eb64" PARTLABEL="HOME"
/dev/sda3: UUID="d50cf8d8-fd62-4384-932d-994f2d59dde5" PARTLABEL="BOOT"

# Add these lines, substituting the UUID's from the output above

luks1 UUID="d50cf8d8-fd62-4384-932d-994f2d59dde5" none luks
luks2 UUID="bc0c4867-6a91-4f2d-a257-4374d3b8a83c" none luks
luks3 UUID="1d1eaa5a-3d67-4568-b4d8-c15a87c7eb64" none luks
swap /dev/mapper/vg_swap-lv_swap /dev/urandom swap,cipher=aes-xts-plain64:sha256,size=512

# The last line will be the encrypted swap, which we need to modify the fstab file to use...

echo /dev/mapper/vg_swap-lv_swap none swap defaults 0 0 >> /etc/fstab

sudo nano /etc/default/grub

GRUB_ENABLE_CRYPTODISK=y
# `GRUB_CMDLINE_LINUX_DEFAULT="loglevel=4 rd.auto=1 cryptdevice=/dev/sda4:root"

sudo cryptsetup luksDump ${DISK}-part3 && sudo cryptsetup luksDump ${DISK}-part4 && sudo cryptsetup luksDump ${DISK}-part5

### RESCUE
sudo su
DISK=$(ls -l /dev/disk/by-id | awk '/sda/ {print "/dev/disk/by-id/"$9}' | head -n 1 )
DEST=/dev/sdb1/luks.key
cryptsetup luksOpen ${DISK}-part3 luks1 --key-file $DEST
cryptsetup luksOpen ${DISK}-part4 luks2 --key-file $DEST
cryptsetup luksOpen ${DISK}-part5 luks3 --key-file $DEST
pvscan
vgscan
lvscan
mount /dev/mapper/vg_root-lv_root
for DIR in proc sys dev /etc/resolv.conf 
do 
    mount --rbind /$DIR /mnt/$DIR 
done
chroot /mnt
mount -a

sudo cryptsetup convert ${DISK}-part1 --type luks1
####

# <name>  <device>     <password>     <options>
# Asks passphrase
#luks1 UUID="d50cf8d8-fd62-4384-932d-994f2d59dde5" none luks
#luks2 UUID="bc0c4867-6a91-4f2d-a257-4374d3b8a83c" none luks
#luks3 UUID="1d1eaa5a-3d67-4568-b4d8-c15a87c7eb64" none luks
# Uses keyfile
luks1 UUID="d50cf8d8-fd62-4384-932d-994f2d59dde5" /keystore/luks.key luks
luks2 UUID="bc0c4867-6a91-4f2d-a257-4374d3b8a83c" /keystore/luks.key luks
luks3 UUID="1d1eaa5a-3d67-4568-b4d8-c15a87c7eb64" /keystore/luks.key luks
# Encryted swap
swap /dev/mapper/vg_swap-lv_swap /dev/urandom swap,cipher=aes-xts-plain64:sha256,size=512
# swap /dev/mapper/vg_swap-lv_swap /dev/urandom swap,cipher=aes-cbc-essiv:sha256,size=256

# fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/vg_root-lv_root /               ext4    errors=remount-ro 0       1
#/dev/mapper/luks1 /boot           ext4    defaults        0       2
# /boot/efi was on /dev/sda1 during installation
UUID=3B24-07E9  /boot/efi       vfat    umask=0077      0       1
/dev/mapper/vg_home-lv_home /home           ext4    defaults        0       2
#/dev/mapper/vg_swap-lv_swap none            swap    sw              0       0
/dev/mapper/vg_swap-lv_swap none swap defaults 0 0
UUID=09660ab9-d621-4752-b1f7-fc1e7118979a  /boot       ext4    defaults      0       2
UUID="4987-2A68"    /keystore    vfat    defaults 0 2

nano /etc/cryptsetup-initramfs/conf-hook
KEYFILE_PATTERN="/keystore/*.key"

```
Remember to change the $DISK variables to what you are installing to, and mix and match what you want to install. This should be way more complex than you need, but examples for what can be done... A good example to modify from.

---

### Post by MAFoElffen on 2024-03-24
Soory, that one does not use debootstrap. (uses the native installer... 

Wait. Here you go:
```

sudo su -
apt install zfsutils-linux debootstrap
ls /dev/disk/by-id
DISK=/dev/disk/by-id/ata-QEMU_HARDDISK_QM00003

Do not do this unless your intention is to wipe/zero a disk!
# wipefs -a $DISK
# blkdiscard -f $DISK
# sgdisk --zap-all $DISK




sgdisk     -n1:0:+750M  -c1:EFI    -t1:EF00 $DISK
sgdisk     -n2:0:+2G    -c2:bpool  -t2:BE00 $DISK
sgdisk     -n3:0:+6G    -c3:swap   -t3:BF02 $DISK
sgdisk     -n4:0:0      -c4:rpool  -t4:BF00 $DISK

zpool create \
    -o ashift=13 \
    -o autotrim=on \
    -O acltype=posixacl -O xattr=sa -O dnodesize=auto \
    -O compression=lz4 \
    -O normalization=formD \
    -O relatime=on \
    -O canmount=off -O mountpoint=/ -R /mnt \
    rpool $DISK-part4

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

UUID=2404

zfs create -o canmount=off -o mountpoint=none rpool/ROOT
zfs create -o mountpoint=/ rpool/ROOT/ubuntu_$UUID

zfs create -o canmount=off -o mountpoint=none bpool/BOOT
zfs create -o mountpoint=/boot bpool/BOOT/ubuntu_$UUID

zfs create -o canmount=off -o mountpoint=none rpool/USERDATA
zfs create -o mountpoint=/home rpool/USERDATA/ubuntu_$UUID

zfs create -o canmount=on \
    -o mountpoint=/root \
    rpool/USERDATA/root_$UUID
chmod 700 /mnt/root

debootstrap noble /mnt

deb http://archive.ubuntu.com/ubuntu noble main rstricted universe mulitverse
deb http://archive.ubuntu.com/ubuntu noble-updates main restricted universe mulitverse
deb http://archive.ubuntu.com/ubuntu noble-backports mian restricted universe multiverse
deb http://security.ubuntu.com/ubuntu noble-security main restricted universe multiverse 

network:
  version: 2
  ethernets:
    enp1s0:
      dhcp4: true


cd /mnt
mount --make-private --rbind /dev  /mnt/dev
mount --make-private --rbind /proc /mnt/proc
mount --make-private --rbind /sys  /mnt/sys
mount --make-private --rbind /run  /mnt/run
chroot /mnt /usr/bin/env DISK=$DISK UUID=$UUID bash --login

apt update
apt install vim nano
apt install openssh-server
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

mkswap -f ${DISK}-part3
echo /dev/disk/by-uuid/$(blkid -s UUID -o value ${DISK}-part3) \
    none swap discard 0 0 >> /etc/fstab
swapon -a

addgroup --system lpadmin
addgroup --system lxd
addgroup --system sambashare

grub-probe /boot
update-initramfs -c -k all
nano /etc/default/grub
# Add init_on_alloc=0 to: GRUB_CMDLINE_LINUX_DEFAULT
# Set: GRUB_TIMEOUT_STYLE=menu
# Set: GRUB_TIMEOUT=5
# Below GRUB_TIMEOUT, add: GRUB_RECORDFAIL_TIMEOUT=5
# Remove quiet and splash from: GRUB_CMDLINE_LINUX_DEFAULT
# Uncomment: GRUB_TERMINAL=console
# Save and quit.

update-grub
 
grub-install --target=x86_64-efi --efi-directory=/boot/efi \
    --bootloader-id=ubuntu --recheck --no-floppy
 
mkdir /etc/zfs/zfs-list.cache
touch /etc/zfs/zfs-list.cache/bpool
touch /etc/zfs/zfs-list.cache/rpool
zed -F &

Verify that zed updated the cache by making sure these are not empty:
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





## RESCUE
sudo su -
apt update
apt install zfsutils-linux
zpool export -a
zpool import -N -R /mnt rpool
zpool import -N -R /mnt bpool
zfs mount rpool/ROOT/ubuntu_2404
zfs mount bpool/BOOT/ubuntu_2404
zfs mount -a

mount --make-private --rbind /dev  /mnt/dev
mount --make-private --rbind /proc /mnt/proc
mount --make-private --rbind /sys  /mnt/sys
mount --make-private --rbind /run  /mnt/run
chroot /mnt /bin/bash --login
mount -a

```
EDIT:
What is missing from that recipe is adding a user.

I do (while still root user in the chroot)
```

username=mafoelffen
adduser $UserName
cp -a /etc/skel/. /home/$username
chown -R $username:$username /home/$username
usermod -a -G adm,cdrom,dip,lpadmin,lxd,plugdev,sambashare,sudo $username

```
Alternately, I also have some recipe's where I use rsync from a temporarily mounted install image, instead of debootstrap...

---

