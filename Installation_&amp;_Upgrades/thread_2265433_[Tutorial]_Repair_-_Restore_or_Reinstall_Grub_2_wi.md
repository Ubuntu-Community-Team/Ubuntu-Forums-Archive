---
title: "[Tutorial] Repair - Restore or Reinstall Grub 2 with a Ubuntu Live CD or USB"
date: 2015-02-15
forum: Installation &amp; Upgrades
---

### Post by actionmystique on 2015-02-15
I couldn't find online the correct procedure for recent Ubuntu releases with a typical installation on an EFI system. The following steps can be applied on an Ubuntu system with at least 2 partitions:
- a boot partition 
- another partition for /. 

I successfully tested them on Ubuntu 14.10:

```
[COLOR=#000000][FONT=Arial]sudo mount /dev/sda2 /mnt                # Mount root (/) partition[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo mkdir -p /mnt/boot/efi                 # Create EFI partition mount point[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo mount /dev/sda1 /mnt/boot/efi   # Mount EFI partition[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]sudo mount --bind /dev /mnt/dev       # Bind the directories that grub needs access to to detect other OS[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo mount --bind /proc /mnt/proc[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo mount --bind /sys /mnt/sys[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo mount --bind /run /mnt/run[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo mount --bind /dev/pts /mnt/dev/pts[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]sudo chroot /mnt                                # Jump to your installation[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]grub-install /dev/sda[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]grub-install --recheck /dev/sda[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]update-grub[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]CTRL-D[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo reboot[/FONT][/COLOR]
```

---

### Post by oldfred on 2015-02-15
For UEFI chroot where you also have the efi partition.
Some users also have a /boot partition which is not normally required with desktop installs. 
Not to be confused with the efi partition which has the boot flag if using gparted or other tools to show boot flags.

If a separate /boot you must mount it also. Where sda# is partition number of /boot. All other partition numbers also then will be different.
sudo mount /dev/sda# /mnt/boot

A very few users also have other system folders as separate partitions. Not sure which may also need to be mounted similarly.

---

### Post by actionmystique on 2015-02-15
Hello oldfred,

Despite what you've just written, if I mount the boot partition with "sudo mount /dev/sda# /mnt/boot", the "grub-install /dev/sda" fails with the error message looking like:
'grub-install: error: cannot find EFI directory"

The steps I've described are the only necessary and sufficient ones.

I'll edit the first post the add the EFI environment.

---

### Post by oldfred on 2015-02-15
You only need to mount a /boot partition if it is a separate partition. Again most installs do not have it as a partition, but just as a folder inside / (root).

Many of the old guides on installing still suggest a /boot partition,but that now almost always creates more issues than it solves. And installs with LVM or LVM with encryption have the /boot. Not many other places require a /boot partition. 
With LVM installs you have both the /efi and the /boot partition.

---

