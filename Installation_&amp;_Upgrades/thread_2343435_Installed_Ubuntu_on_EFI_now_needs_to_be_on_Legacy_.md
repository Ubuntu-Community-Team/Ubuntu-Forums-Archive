---
title: "Installed Ubuntu on EFI now needs to be on Legacy boot"
date: 2016-11-16
forum: Installation &amp; Upgrades
---

### Post by a1074938 on 2016-11-16
Hi,

I needed a new system to match an existing setup in every way so cloned the drive using clonezilla.

The clone completed fine and both original disk and cloned drive work fine on the original computer.

When transferring the drive to the new machine I am unable to boot from either drive, since both drives are known to contain a functional OS it can only be the second computer.

Managed to run boot repair disk and was told: Boot of the PC is in Legacy mode please change it to EFI. I assume the original computer OS was installed in EFI mode but the target destination for the clone is slightly older so may be using Legacy in bios as I cant see any EFI options in setup. Is there any way to change the boot of the cloned drive to accpet legacy boot?

---

### Post by kpatz on 2016-11-16
Connect the drive to the "new" machine and boot from a live CD or USB.  Install gdisk (terminal) or gparted (GUI) and run it.  Change your EFI partition to a BIOS partition (change its type to EF02).  Note which partition is the root (for my examples we'll assume it's /dev/sda1).  Save the partition table and exit.

Next, mount the root partition:  ```
sudo mount /dev/sda1 /mnt
```

Next, mount the special directories under /mnt:

```
sudo mount --bind /dev /mnt/dev
sudo mount --bind /dev/pts /mnt/dev/pts
sudo mount --bind /sys /mnt/sys
sudo mount --bind /proc /mnt/proc
sudo mount --bind  /run /mnt/run
```

Edit your /etc/fstab to remove the entry for /boot/efi:```
sudo nano /mnt/etc/fstab
```  Comment-out or delete the line that mounts /boot/efi and save the file.

Chroot to your mounted drive:```
sudo chroot /mnt
```You'll be in a root prompt with your mounted drive at /.

Install BIOS grub to replace EFI grub:```
apt-get update && apt-get install --reinstall grub-pc
```

Setup and install grub:```
update-grub
grub-install /dev/sda
```

Exit the chroot:```
exit
```

Unmount everything you mounted earlier:

```
sudo umount /mnt/dev/pts /mnt/dev /mnt/sys /mnt/proc /mnt/run
sudo umount /mnt
```

Shut down the live session and remove the CD or USB, reboot and cross your fingers. :)

---

### Post by oldfred on 2016-11-16
If new system just set for BIOS boot and needs to be UEFI?
New UEFI systems have three ways to boot UEFI with Secure boot, UEFI, and BIOS/CSM.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

I would check that you have UEFI/BIOS set to boot in correct mode. If system is really BIOS only then it is not very new as all systems with Windows 8, Oct 2012 or later have been UEFI.

While you can convert a MBR(msdos) partitioned drive to gpt(GUID) partitioned drive (or vice-versa), you have to reinstall grub and edit fstab with new UUIDs. And it may not always work.
And Windows only boots in BIOS mode from MBR and only in UEFI mode from gpt.

---

### Post by a1074938 on 2016-11-17
@[COLOR=#000000]kpatz - Thanks for the comprehensive reply, I will give this a try this morning.[/COLOR]

@odlfred - The 'new' system is a refurbished HP workstation. It has 96GB RAM rather than the 16GB of the desktop computer I have cloned. I now need access to this RAM for processing data. 

Prior to cloning I overlooked the issue of boot type as it hadn't crossed my mind.

From what I have read the high RAM workstation does not support UEFI boot.

---

### Post by oldfred on 2016-11-17
Often high end systems supported UEFI before standard desktops. 
If your system does not support UEFI and drive is UEFI/gpt you can add a 1 or 2MB unformatted partition with the bios_grub flag. And then install grub-pc.
Boot-Repair can do the full uninstall of grub-efi-amd64(UEFI) and reinstall of grub-pc(BIOS).

---

