---
title: "Scripts to partially automate Ubuntu 18.04 on ZFS installation"
date: 2018-07-14
forum: Installation &amp; Upgrades
---

### Post by averyfreeman on 2018-07-14
Have some fairly rudimentary scripts I threw together while installing Ubuntu 18.04 on ZFS using a live ISO flash drive. 

This definitely makes things easier for me and MUCH faster than going step-by-step.  But make sure you understand what each command does and verify that it's what you want if you're going to try it.

I recommend you ONLY use it on a system with just ONE DRIVE you're going to dedicate to Ubuntu unless you really know what you're doing - and even then, you'll have to modify it quite a bit.

Also, this is completely unsupported by Canonical.  According to them:

[COLOR=#000000]*ZFS*[/COLOR]
[COLOR=#000000]*ZFS support was added to Ubuntu Wily 15.10 as a technology preview and comes fully supported in Ubuntu Xenial 16.04. Note that ZFS is only supported on 64 bit architectures. Also note that *[/COLOR][B]ZFS is only supported for data storage, not the root filesystem.

[/B]However, my belief is that zfs snapshots are incredibly helpful for management of root filesystems.  I do not work for, nor am I affiliated with, Canonical in any way.

YOU HAVE BEEN WARNED!


Adapted from this how-to:
[https://github.com/zfsonlinux/zfs/wiki/Ubuntu-18.04-Root-on-ZFS](https://github.com/zfsonlinux/zfs/wiki/Ubuntu-18.04-Root-on-ZFS)

If you want more granular detail or a LUKS installation, or a BIOS installation rather than EFI, you can check there and do it step by step.

Or you can just install it without encryption using EFI by copying my scripts here and running them. 

Sound good? OK! Let's get started  -


Download live ISO for desktop here:
[https://www.ubuntu.com/download/desktop](https://www.ubuntu.com/download/desktop)


Note: Will not work with 'live server' ISO.


Instructions: 


Boot ISO -

select try ubuntu

select live user


commands - run:


ctrl-alt-t [to open terminal] 

```

passwd [enter passwd for ubuntu user]
sudo su root
apt install -y openssh-server
ip addr

```

From another computer, log into the system running the live ISO: 

```

ssh ubuntu@[ip addr]
sudo su root

```



Copy this script and run from ssh terminal --- there's a few things you'll likely have to change in the script:

1) paste it into nano and use ctrl-\ to find-and-replace your boot drive assignment after identifying it with lsblk.
2) change /etc/netplan/controllername.yaml to reflect your device name desired network settings

```



#!/bin/bash
# init
function pause(){
   read -p "$*"
}
 
# ...
# call it
pause 'NOTE: Will pause occasionally to verify stuff. If you're awake, press [Enter] key to continue or CTRL-C to abort and re-tool the rest of the script'
# ...
add-apt-repository universe
apt update
apt install -y openssh-server zfs-initramfs gdisk debootstrap


#This clears the disk 
pause 'Press any key to clean /dev/sda - CTRL-C to abort'
sgdisk --zap-all /dev/sda
apt install zfs-initramfs gdisk debootstrap
echo 'create efi partition'
sgdisk     -n3:1M:+512M -t3:EF00 /dev/sda
echo 'prep empty space for zfs'
sgdisk     -n1:0:0      -t1:BF01 /dev/sda


zpool create -f -o ashift=12 \
      -O atime=off -O canmount=off -O compression=lz4 -O normalization=formD \
      -O xattr=sa -O mountpoint=/ -R /mnt \
      rpool /dev/sda1


zfs create -o canmount=off -o mountpoint=none rpool/ROOT
zfs create -o canmount=noauto -o mountpoint=/ rpool/ROOT/ubuntu
zfs mount rpool/ROOT/ubuntu


zfs create                 -o setuid=off              rpool/home
zfs create -o mountpoint=/root                        rpool/home/root
zfs create -o canmount=off -o setuid=off  -o exec=off rpool/var
zfs create -o com.sun:auto-snapshot=false             rpool/var/cache
zfs create -o acltype=posixacl -o xattr=sa            rpool/var/log
zfs create                                            rpool/var/spool
zfs create -o com.sun:auto-snapshot=false -o exec=on  rpool/var/tmp


#only necessary if doing by hand:
lsblk
zpool list
zfs list
pause 'Verify correct - press key to continue, CTRL-C to abort'
chmod 1777 /mnt/var/tmp
debootstrap bionic /mnt
zfs set devices=off rpool


cat >> /mnt/etc/netplan/ens192.yaml << EOF


network:
 version: 2
 renderer: networkd
 ethernets:
   ens192:
     dhcp4: no
     dhcp6: no
     addresses: [192.168.1.42/24]
     gateway4: 192.168.1.1
     nameservers:
       addresses: [192.168.1.2,192.168.1.3]
EOF


cat /mnt/etc/netplan/ens192.yaml


pause 'Verify correct - press key to continue, CTRL-C to abort'


cat > /mnt/etc/apt/sources.list < EOF


deb http://archive.ubuntu.com/ubuntu bionic main universe
deb-src http://archive.ubuntu.com/ubuntu bionic main universe


deb http://security.ubuntu.com/ubuntu bionic-security main universe
deb-src http://security.ubuntu.com/ubuntu bionic-security main universe


deb http://archive.ubuntu.com/ubuntu bionic-updates main universe
deb-src http://archive.ubuntu.com/ubuntu bionic-updates main universe
EOF


cat /mnt/etc/apt/sources.list


pause 'Verify correct - press key to continue, CTRL-C to abort'


mount --rbind /dev  /mnt/dev
mount --rbind /proc /mnt/proc
mount --rbind /sys  /mnt/sys
chroot /mnt /bin/bash --login


---- end first part of script

```

You're now in chroot so you can't just run one script all the way through -
Manually run: 

```

apt update && apt install -y nano

```

Then copy and paste this like you did in the first part - don't forget to replace your drive assignment first to the drive you used in the previous script:


```

script part two, -------------




#!/bin/bash
# init
function pause(){
   read -p "$*"
}
 




ln -s /proc/self/mounts /etc/mtab
#apt update
apt upgrade -y
apt install -y locales


#interactive:
#dpkg-reconfigure locales 
#non-interactive:
LANG=en_US.UTF-8 locale-gen --purge en_US.UTF-8


#Revisit this - not working properly 0 non-interactive:
#echo "America/Los_Angeles" > /etc/timezone
#dpkg-reconfigure -f noninteractive tzdata 
#interactive:
dpkg-reconfigure tzdata 


# install zfs in chroot environment (complete in these steps)
apt install -y --no-install-recommends linux-image-generic
apt install -y zfs-initramfs dosfstools open-vm-tools


lsblk


pause 'going to make partition 3  EFI partition and install grub -- press key'


mkdosfs -F 32 -n EFI /dev/sda3
mkdir /boot/efi
echo PARTUUID=$(blkid -s PARTUUID -o value /dev/sdb3) /boot/efi vfat nofail,x-systemd.device-timeout=1 0 1 >> /etc/fstab


mount /boot/efi
cat /proc/mounts | grep /dev/sda3


pause 'is /dev/sda3 mounted to /boot/efi? Press a key...'


apt install -y grub-efi-amd64


addgroup --system lpadmin
addgroup --system sambashare
addgroup sudo
useradd local
passwd local
passwd
hostname ubuntuzfs




echo '%sudo ALL=ALL(ALL)' > /etc/sudoers.d/sudo
echo 'local ALL=ALL(ALL)' > /etc/sudoers.d/local




zfs set mountpoint=legacy rpool/var/log
zfs set mountpoint=legacy rpool/var/tmp
cat >> /etc/fstab << EOF
rpool/var/log /var/log zfs defaults 0 0
rpool/var/tmp /var/tmp zfs defaults 0 0
EOF
cat /etc/fstab
pause 'does /etc/fstab look okay? Press key...'


grub-probe / 
# should return: zfs
pause 'does it return "zfs"??? Press a key...'
update-initramfs -c -k all


grub-install --target=x86_64-efi --efi-directory=/boot/efi \
      --bootloader-id=ubuntu --recheck --no-floppy


ls /boot/grub/*/zfs.mod
pause 'should return: /boot/grub/x86_64-efi/zfs.mod -- almost done!  Press a key...'


pause 'want to install virtualization and container software?? if so, press a key - if not, ctrl-C'


apt install -y openssh-server putty-tools lxc lxd ifupdown lxctl lxc-templates python3-dev seccomp python-gnutls gnutls-bin virt-manager virt-top virtinst  libvirt-daemon* libvirt-bin libvirt-clients gparted ssh-askpass git guestfsd libguestfs-zfs zfs-fuse


---- end script 2

```





5.3 Optional (but highly recommended): Make debugging GRUB easier:


nano /etc/default/grub

#Comment out: GRUB_HIDDEN_TIMEOUT=0
#Remove quiet and splash from: GRUB_CMDLINE_LINUX_DEFAULT
#Uncomment: GRUB_TERMINAL=console
#Save and quit.


#Update the boot configuration and install grub:

```

update-grub

```

#Take your first snapshot: 

```

zfs snapshot rpool/ROOT/ubuntu@install

```

#Verify that the ZFS module is installed:

```

ls /boot/grub/*/zfs.mod

```

#should return: /boot/grub/x86_64-efi/zfs.mod


Note: You do NOT want to reboot before that last command gives you the correct result.  If it doesn't, you're likely going to reboot to brick.   If there's a problem, be sure to go back over the code and try and find anything that went wrong and do it again, or just run the whole thing over again (will likely have to reboot and clear drive again if you're all the way in chroot).  


---- still need to do the below steps before you can cleanly reboot ---- 


#Exit chroot and umount zfs stuff, export rpool

```

exit 
mount | grep -v zfs | tac | awk '/\/mnt/ {print $3}' | xargs -i{} umount -lf {}
zpool export -f rpool

```


reboot


Enjoy your ZFS-on-root Ubuntu 18.04!

What do you think, is there anything you recommend I should change?

---

### Post by TheFu on 2018-07-14
A warning would be helpful. ZFS should be used for data, not the OS if stability is the primary goal or it is a production system.

[https://wiki.ubuntu.com/Kernel/Reference/ZFS](https://wiki.ubuntu.com/Kernel/Reference/ZFS) says:
> ZFS
ZFS support was added to Ubuntu Wily 15.10 as a technology preview and comes fully supported in Ubuntu Xenial 16.04. Note that ZFS is only supported on 64 bit architectures. Also note that **ZFS is only supported for data storage, not the root filesystem. **

---

### Post by averyfreeman on 2018-07-14
Very true!  It is definitely not supported for root filesystems, although it is arguably very helpful to have for snapshots - still looking for a replacement for beadm like Solaris.  I will use your language if you don't mind.

---

### Post by fields-g on 2018-07-26
I have two other methods for 18.04 ZFS on Root install:
1) Manual Method -- [https://github.com/zfsonlinux/pkg-zfs/wiki/HOWTO-install-Ubuntu-18.04-to-a-Whole-Disk-Native-ZFS-Root-Filesystem-using-Ubiquity-GUI-installer](https://github.com/zfsonlinux/pkg-zfs/wiki/HOWTO-install-Ubuntu-18.04-to-a-Whole-Disk-Native-ZFS-Root-Filesystem-using-Ubiquity-GUI-installer)
2) Scripted Method --[ https://github.com/ghfields/rpooler]("http://https://github.com/ghfields/rpooler")

The scripted version is more feature rich and foolproof.

---

