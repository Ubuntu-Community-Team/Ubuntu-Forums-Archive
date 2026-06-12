---
title: "Cannot mount btrfs inside LUKS"
date: 2021-05-23
forum: Installation &amp; Upgrades
---

### Post by liubomirwm on 2021-05-23
Hello!

I have been following [THIS]("https://mutschler.eu/linux/install-guides/ubuntu-btrfs/") tutorial and trying to install Kubuntu with btrfs and encrypted /boot partition.
Instead of using parted or gparted, i decided to use gnome-disk-utility for creating the partitions.
Using gnome-disks, i've created the following partitions:
[LIST]
[*]dev/sda1 - EFI system partition, In gnome-disks i formatted as FAT32 EFI System. 
[*]dev/sda2 - to be used as /boot partition. In gnome-disks i formatted with selection as "No filesystem", effectively just setting its size 
[*]dev/sda3 - to be used as root partition. In gnome-disks i formatted with selection as "No filesystem", effectively just setting its size. 
[*]/dev/sda4 - 8GB to be used as swap partition. In gnome-disks i formatted with selection as "No filesystem", effectively just setting its size. 
[/LIST]
[FONT=monospace][COLOR=#000000]
After that i run the following commands:
[LIST]
[*]sudo cryptsetup luksFormat --type=luks1 /dev/sda2 
[*]sudo cryptsetup luksFormat --type=luks2 /dev/sda3 
[/LIST]
Then:
[LIST]
[*]sudo cryptsetup luksOpen /dev/sda2 sda2_crypt 
[*]sudo cryptsetup luksOpen /dev/sda3 sda3_crypt 
[/LIST]
This created /dev/mapper/sda2_crypt and /dev/mapper/sda3_crypt

Then in Kubuntu installer -> Disk Setup -> Manual -> Prepare partitions i had the following devices
[LIST]
[*]/dev/mapper/sda2_crypt 
[*]/dev/mapper/sda3_crypt 
[*]/dev/sda
[LIST]
[*]/dev/sda1 
[*]/dev/sda2 
[*]/dev/sda3 
[*]/dev/sda4 
[/LIST]
   
[/LIST]

I clicked on the line that said [FONT=monospace][COLOR=#000000]/dev/mapper/sda2_crypt and the installer asked me something along the lines of "You have selected a device, the installer will create a partition", though i'm not 100% sure about the "partition" part. I clicked ok and now it was showing this:
[/COLOR][/FONT]
[LIST]
[*][FONT=monospace][COLOR=#000000]/dev/mapper/sda2_crypt[/COLOR][/FONT]
[LIST]
[*][FONT=monospace][COLOR=#000000]free space[/COLOR][/FONT] 
[/LIST]
   
[/LIST]
[FONT=monospace][COLOR=#000000]Now i selected "free space"[/COLOR][/FONT], clicked "Change", selected "Use as ext4" and for mount point "/boot". I ticked "Format" checkbox.

For the line that said [FONT=monospace][COLOR=#000000][FONT=monospace][COLOR=#000000]/dev/mapper/sda3_crypt[/COLOR][/FONT][/COLOR][/FONT] i did the same, however there i selected "Use as btrfs journalled-filesystem" and mount point "/" (the root).

Then i selected install.
After that i followed the steps in the tutorial - mounting btrfs (successfully), creating chroot, crypttab and encrypting swap.
Then i installed grub exactly as shown in the tutorial.

I restarted and was greeted with a warning triangle icon and big text "Security boot fail". I thought/took a guess that this was because i have Secure Boot enabled and because shim has not been explicitly installed as per the tutorial steps. Before i restarted and the error came up, i did not check whether shim was in fact installed along with grub (had no problems = no reason to).

Now i want to boot the live USB again and unlock LUKS, mount btrfs, chroot and install shim (while writing this i'm also thinking of simply disabling Secure Boot to see whether the new installation will boot, but i don't do this yet).
So i manage to boot the live USB and to unlock LUKS.
Then i try to run the command "[FONT=monospace][COLOR=#000000]sudo mount -t btrfs -o subvol=@ /dev/mapper/sda3_crypt /mnt[/COLOR][/FONT]" but i get the following error:
[FONT=monospace][COLOR=#000000]mount: /mnt: wrong fs type, bad option, bad superblock on /dev/mapper/sda3_crypt, missing codepage or helper program, or other error.[/COLOR]
Now i have collected some screenshots to show the current state of the system, please see them [HERE]("https://imgur.com/a/6ZK53wh").[/FONT]

Now i tried to run "[FONT=monospace][COLOR=#000000]sudo mount -t btrfs -o subvol=@ /dev/mapper/sda3_crypt1 /mnt[/COLOR][/FONT]", but now i get this error:
mount: /mnt: special device /dev/mapper/sda3_crypt1 does not exist.[/COLOR]

Please, can someone more knowledgeable than me tell me what have i done/am i doing wrong?
[/FONT]

---

### Post by liubomirwm on 2021-05-23
The output of sudo blkid /dev/mapper/sda3_crypt is:
/dev/mapper/sda3_crypt: PTUUID="26a10fce-03ef-4e5e-be5b-7a85ded76c37" PTTYPE="gpt"

---

