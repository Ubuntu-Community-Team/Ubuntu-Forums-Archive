---
title: "Installing an encrypted /, /home and swap while preserving existing partitions"
date: 2016-01-08
forum: Installation &amp; Upgrades
---

### Post by Gijsbert_Wiesenekk on 2016-01-08
Hi,

I wanted to switch from an encrypted home directory to fully encrypted /, /home and swap partitions while preserving two other existing partitions. The installer only gives you the option to erase the entire disk if you want to encrypt the Ubuntu installation, and if you choose 'Something else' you cannot choose an encryption method. If you Google how to continue the instructions are not always up-to-date or incomplete, often resulting in a system that either does not boot or does not prompt for the password to unlock the partitions at boot. It took me a couple of hours to get it working so I am posting these instructions now for reference if you want a similar setup. The following instructions have been tested against Ubuntu 14.04.3:

The scenario:
I had an existing Ubuntu installation with a btrfs root partition / (/dev/sda1) and a swap partition (/dev/sda2) that I wanted to replace and two more partitions /dev/sda3 and /dev/sda4 that I wanted to preserve.
# Boot from the Ubuntu Live CD and choose 'Try Ubuntu'.
# Start gparted, delete the /dev/sda1 and /dev/sda2 partitions, create a /dev/sda1 partition with label '/boot' and a size of 256MB and a /dev/sda2 partition with label 'rootvg' in the remaining space.
# Open a terminal and encrypt the /dev/sda2 partition that will contain the volume group rootvg:
$ sudo cryptsetup -y -v -s 512 luksFormat /dev/sda2
$ sudo cryptsetup luksOpen /dev/sda2 rootvg
# Create the volume group 'rootvg' and create the logical volumes 'swap' and 'root' in the volume group:
$ sudo vgcreate rootvg /dev/mapper/rootvg
$ sudo lvcreate -n swap -L <Desired size of the swap logical volume in Gigabytes>g rootvg
#Check how many Physical Extents are left in the volume group:
$ sudo pvdisplay
# Create the root logical volume in the remaining space:
$ sudo lvcreate -n root -l <Free PE number shown in the output of pvdisplay command> rootvg

Start the installer and install Ubuntu, choose 'Something else' as Installation type, select /dev/sda1 as /boot, /dev/mapper/rootvg-root as / and /dev/mapper/rootvg-swap as swap. I use btrfs for the / partition. Do NOT reboot after installation.
Switch back to the terminal and get the blkid of the encrypted partition:
$ sudo blkid /dev/sda2
# Prepare for update-initramfs
# If you used ext4 for the root partition you can use mount -t ext4 /dev/rootvg/root /mnt
$ sudo mount -t btrfs -o subvol=@ /dev/rootvg/root /mnt
$ sudo mount /dev/sda1 /mnt/boot
$ sudo mount --bind /dev /mnt/dev
$ sudo mount --bind /proc /mnt/proc
$ sudo mount --bind /sys /mnt/sys
$ sudo echo "rootvg UUID=<UUID shown in the output of the blkid command without quotes> none luks,discard" | sudo tee /mnt/etc/crypttab
$ sudo chroot /mnt
$ update-initramfs -k all -c -v
$ exit
# Prepare for reboot:
$ sudo umount /mnt/sys
$ sudo umount /mnt/proc
$ sudo umount /mnt/dev
$ sudo umount /mnt/boot
$ sudo umount /mnt
$ sudo swapoff -a
$ sudo vgchange -a n rootvg
$ sudo cryptsetup luksClose rootvg

Reboot and you will be prompted for the password to unlock the root volume group!

Regards,
Gijsbert

---

### Post by Gijsbert_Wiesenekk on 2016-05-15
I just verified that these instructions also work for a fresh install of Ubuntu 16.04. If you were already running a similar setup you can import the existing volume group:

$ sudo cryptsetup luksOpen /dev/sda2 rootvg
$ sudo vgchange -a y rootvg

and start the installation.

Regards,
Gijsbert

---

