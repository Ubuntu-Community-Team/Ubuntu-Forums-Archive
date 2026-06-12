---
title: "Change Ubuntu boot to use its own EFI partition"
date: 2022-08-16
forum: Installation &amp; Upgrades
---

### Post by Mark Phelps on 2022-08-16
I have multiple SSDs, each formatted GPT, each with its own EFI partition.

I am new to UEFI and EFI, so I am stumbling around here...

When I installed Mint, despite my pointing to /sdb3 (the Linux SSD EFI partition), it wrote its boot files to the nvme1 (Windows) EFI partition -- but that boots OK and allows me to select Ubuntu, Mint or any of the Windows drives.

But later, I installed Ubuntu and while it thought it installed its boot files to its own EFI partition on the Linux drive, the displayed boot text menu is actually from the EFI partition (on the Windows drive).

I only discovered this because I installed Plymouth in Ubuntu and the boot splash only appears during shutdown, not during boot.

I mounted the EFI partition from the Linux drive and it is empty, so will the following be sufficient to change the booting to that drive from the Windows drive:
-- Copy the boot and ubuntu folders from the Windows drive EFI partition to the Linux drive EFI partition
-- Change the FSTAB boot entry to use the UUID of the Linux drive EFI partition
-- Run sudo update-grub

Or is there more that I need to do??

Also, after I do that, I presume if I then do an update-grub, it will discover the Mint install on the same drive and add that to grub.cfg, right?

---

### Post by oldfred on 2022-08-16
Any offical Ubuntu install or unofficial version that uses Ubiquity installer has this bug.
Posted work around to manually unmount & mount correct ESP during install #55 or( #23 & #26)
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall of grub to correct drive. 

If you have an ESP on drive with the Ubuntu you want, just edit fstab with correct UUID of that fstab and do a full reinstall of grub. A update only update grub menu not boot files in ESP.
This installs to ESP mounted in fstab, if already UEFI install. Conversion from BIOS or grub-pc may need additional settings.

```
[FONT=monospace][COLOR=#54ff54]**fred@z690-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo grub-install [/COLOR]
[sudo] password for fred:  
Installing for x86_64-efi platform. 
Installation finished. No error reported.
[/FONT]
```

If menu needs update:
sudo update-grub

Grub can install to any drive's ESP if directed there. If using external drive, you have to use Boot-Repair or chroot to have correct partitions used. And then various options in grub install may be required.

See also:
man grub-install

To confirm UEFI boot files, you can check UEFI settings. UEFI uses GUID or partuuid to know which ESP/FAT32 partition to find boot files.
You can compare partUUID before & after:
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid
with this which will show UEFI entry using partUUID.
sudo efibootmgr -v

---

### Post by tea for one on 2022-08-16
> **oldfred said:**
> Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive
This is my preferred method i.e. only the target drive is visible.
The added advantage of an ESP on each disk is that you can always boot from UEFI one-time menu.
> **oldfred said:**
> Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
I could not get this to work using Gparted in Ubuntu 20.04 but I have had success with Gparted in 22.04
If you have three drives, you have to remove boot and esp flag from the two drives you want to remain invisible.

---

### Post by Mark Phelps on 2022-08-16
@oldfred:

Thanks very much for your help -- as that has fixed the issue and I am now booting from the Linux SSD.

---

