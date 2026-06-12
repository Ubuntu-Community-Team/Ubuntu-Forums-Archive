---
title: "Ubuntu not starting after installing Kubuntu (grub problem)"
date: 2011-09-23
forum: Installation &amp; Upgrades
---

### Post by atti84it on 2011-09-23
Apparently Kubuntu has wiped the grub entry for my old Ubuntu partition and I'm trying to restore it.

I've been using Ubuntu for a long time (11.04), then I dual booted with Kubuntu but grub doesn't allow me to choose Ubuntu. Now I can only boot Kubuntu. I want my Ubuntu back! (with all my files)

I've added timeout to /etc/default/grub:

[INDENT]GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR='`lsb_release'
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_DEFAULT='Ubuntu, with Linux 2.6.38-11-generic'
GRUB_CMDLINE_LINUX_DEFAULT='quiet splash'
GRUB_HIDDEN_TIMEOUT=10
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_CMDLINE_LINUX=''[/INDENT]

I've done sudo upgrade-grub but it only finds the Kubuntu kernels:

[INDENT]Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-11-generic
Found initrd image: /boot/initrd.img-2.6.38-11-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
done[/INDENT]

I've added an executable file: /etc/grub.d/08_ubuntu whose content is:

[INDENT]#!/bin/sh -e
echo "Adding my custom Linux to GRUB 2"
cat << EOF
menuentry "My custom Linux" {
linux (hd0,1)/boot/vmlinuz-2.6.38-11-generic root=UUID=b838444f-a368-49ef-937e-25df5b29b435 ro quiet splash
initrd (hd0,1)/boot/initrd.img-2.6.38-11-generic
}
EOF[/INDENT]

but no luck :(

The begin of Boot Info Script is:

[INDENT]                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda2: __________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info:  

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img[/INDENT]

So my OS is actually there but I don't know how to tell to grub to link it in boot menu!!

NOTE:
sda1 is /boot of my old ubuntu
sda2 is the encrypted LUKS-LVM root partition
sda6 is the working kubuntu

---

### Post by atti84it on 2011-09-24
I solved it!! Here the commands for the terminal:

```
sudo -s

# IF YOU DON'T HAVE A LUKS-LVM PARTITION:
mount /dev/sda2 /mnt
mount /dev/sda1 /mnt/boot  # skip this one if not have a separate /boot partition
grub-install --root-directory=/mnt/ /dev/sda

# IF YOU HAVE A LUKS-LVM PARTITION:
cryptsetup luksOpen /dev/sda2 sda2_crypt
# I got a weird warning (something about semaphores, bug #719388 on launchpad). Just ignore it.

mount /dev/<lvm-group-name>/<lvm-volume-name> /mnt
# in my case: mount /dev/volumi/root /mnt

mount /dev/sda1 /mnt/boot

grub-install --root-directory=/mnt/ /dev/sda
```

---

