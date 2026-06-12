---
title: "Going from triple boot to dual boot, and moving partitions around on hard drive"
date: 2015-05-23
forum: Installation &amp; Upgrades
---

### Post by PatrickD-52761 on 2015-05-23
Hi everyone,

So here's my situation. I have a triple boot on my laptop. Windows 8.1, Ubuntu 14.04, and Fedora 19. I hardly ever use the Fedora boot, so I want to remove it. Plus, I want to move my Ubuntu partitions over, so I can allocate some of the freed up space to both it, and Windows 8.1. All of this is on a Toshiba Satellite with UEFI (not secure boot) set up.

So my questions are, is this as simple as I think? I'm thinking it's a matter of removing the partitions for Fedora/swap, updating grub, then probably rebooting, and then moving/resizing the free space as necessary. Then updating Grub again and rebooting.

Or would I remove Fedora, update Grub, then reboot, and move the partitons and update grub again, then boot into Windows and use it to resize it's partition?

Or, would I do it completely different altogether? My goal is to not lose any data, except whatever is on the Fedora partition.

Thanks, and have a great day.:)
Patrick.

---

### Post by grahammechanical on 2015-05-23
It all depends on which Linux is in charge of the Grub boot menu. If Fedora is in charge of the boot menu, then removing Fedora will break the boot menu. You need to first load Ubuntu and run

```
sudo grub-install /dev/sda
```

to put Ubuntu in charge of the boot menu. Then after removing Fedora you load into Ubuntu and run

```
sudo update-grub
```

to clear Fedora out of the Grub boot menu list. You may find that UEFI still has Fedora in its listing. I do not have a UEFI machine so I cannot help you there.

Regards.

---

### Post by oldfred on 2015-05-23
Generally you want to make sure grub is working from the install(s) you are keeping first.
But with UEFI, UEFI has NVRAM and efi partition has boot files that are kept even when you remove an install's partition. You must separately houseclean the efi partition's folder and use efibootmgr to remove entry from UEFI.

Is you Fedora install, an LVM install? 
Have you backed up any data in it.
Generally best to update your backups before any major system change.

I generally do not like to move the start of partitions. All data has to be copied, so any interruption will corrupt data and if a lot of data it can take a while. Again good backups.

I might just convert current Fedora partition(s) to a new NTFS data partition.
Post this and what you are thinking about changing?
sudo parted -l

---

