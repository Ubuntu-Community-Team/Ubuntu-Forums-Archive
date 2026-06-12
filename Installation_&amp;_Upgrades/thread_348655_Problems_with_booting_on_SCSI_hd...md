---
title: "Problems with booting on SCSI hd.."
date: 2007-01-29
forum: Installation &amp; Upgrades
---

### Post by dupa on 2007-01-29
I have an old server with two SCSI disks connected to an old SCSI RAID pci card.

There is not the bios support for linux, in order to have "hardware raid" in Linux, but ok. it's not a problem for me. I will use the 2 disks as separeted entities.

During the ubuntu installation the partitioner SEE both /dev/sda and both /dev/sdb (I see them as separeted disk.. so the hw raid don't work!)

I can partition them as I want, and i begin the installation process.
I can see the hd led is blinking.. so data is being written there. very well.

When the installer install GRUB, on the screen don't appear any error message.
The fact is that when i reboot the machine... the bootloader is NOT found.

I want to create a floppy disk for booting. can you give me any  link to guides, tutorials and stuff like that?
thanks.

---

