---
title: "Can I instal Ubuntu on a non-bootable drive ?"
date: 2020-05-04
forum: Installation &amp; Upgrades
---

### Post by nola-guy on 2020-05-04
Newbie here. I was surprised I couldn't find this in a search, since I would think it would be a common situation.I have an older system that is plenty fast enough, but it only has sata2 and does not support pci-e booting. So my new SSD is bottle necked by the sata2. If I install grub on a drive the bios sees as bootable, can Ubuntu and W10 be on the SSD connected to a pci-e card the bios can't boot from?

---

### Post by oldfred on 2020-05-04
I do not have previous posts.
But have seen users with drives in removable DVDs that would not boot, and install to that drive. But I think one only needed grub on bootable drive, but another user had to have both grub & a /boot partition on bootable drive. 

No idea on Windows.

---

### Post by sudodus on 2020-05-04
I have such a system with the bootloader and a boot partition on the bootable drive, but the root partition on the fast nvme drive, which is not recognized as a boot device, but works well for the root partition.

This is straight-forward to install with the installer Ubiquity (used by all desktop flavours except Lubuntu). The old Debian installer in the classic Ubuntu Server and in Ubuntu mini.iso can do it too.

Lubuntu's Calamares couldn't do it when I tried a few months ago. I don't know about the new Curtin installer in Ubuntu Live Server.

---

### Post by nola-guy on 2020-05-04
What about my W10?

---

### Post by CelticWarrior on 2020-05-04
> **nola-guy said:**
> What about my W10?

Should work but old = BIOS therefore likely more complicated. You need to install Windows first.

---

### Post by sudodus on 2020-05-04
There are other forums where you can get better help with Windows ;-)

[hr][/hr]
But if you are thinking about dual booting with Ubuntu, we can help :-)

You can keep Windows where it is.

- Backup everything that you cannot afford to lose, maybe the while drive with Windows, maybe only your personal files: documents, pictures etc.

- When running Windows, shrink the Windows partition so that there will be space enough for a boot partition. The size should be at least 500 MB but I suggest 1 GB to decrease the risk that it will get full in the future. Leave unallocated drive space.

- Then boot into the Ubuntu live drive.

- Create a partition with an ext4 file system in the unallocated space that was created when you shrank the Windows partition. You can do this NOW with gparted or later with the installer.

- Start the installer. At the partitioning table you select 'Something else' alias manual partitioning and set up the partitions and select them to fit what you want.

- If booted in BIOS mode (alias CSM alias legacy mode), you can control where to install the bootloader. Obviously it should be at the head end of the bootable drive. In UEFI mode this will be automatic (even if you triy something else).

- After that the installation is rather straight-forward.

---

### Post by nola-guy on 2020-05-04
I think you missed my question. I already installed Ubuntu on a partition of drive 0. I was wanting to get full speed out of my SSD by adding a sata 3 adapter. But I can't boot off of pcie sata adapters. Can I put Grub on a drive I can boot from, then put Linux  on the drive connected to un-bootable  the pci card?

---

### Post by ubfan1 on 2020-05-05
As long as grub can see the drive, it can run the kernel and mount a filesystem from it. I had an odd situation once, where I had to boot grub off a USB to run a disk in a DVD caddy.  For some reason, the boot ordering did not work when trying to make grub boot off the first hard disk -- grub would hang, not display any menu, and all disk lights would be on.  With the USB first in boot order, booting from the USB kept grub from accessing the hard disks until it was finished setting itself up, then it could successfully boot root on either disk.

---

