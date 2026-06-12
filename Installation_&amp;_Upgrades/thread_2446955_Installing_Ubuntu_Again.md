---
title: "Installing Ubuntu Again"
date: 2020-07-09
forum: Installation &amp; Upgrades
---

### Post by Shmoogly on 2020-07-09
Hi, I got a new computer and am installing everything again. My motherboard has 6 SATA ports which I have used up for my W10 install. I purchased an additional PCI RAID controller card with an additional 4 SATA ports. I connected two new HDDs to this SATA card and configured them as RAID 1. I want to install Ubuntu onto these two drives. I managed to install Linux onto this RAID 1 partition by unplugging the 6 HDDs from the motherboard that have W10 on them, however my BIOS doesn't see the RAID card or the HDDs connected to it, so I can't boot into the installed Ubuntu. Windows sees this partition and the Ubuntu installer sees this partition also.

I tried installing Ubuntu with all the HDDs plugged in, and based on my reading, all that I need to do is to setup the partitions on my newly created RAID 1 partition for Ubuntu (for example):

    /boot           1 GB (ext4 files system)
    /home         18 GB (ext4 file system)
    /                  12 GB (ext4 file system)
    /var             6 GB (ext4 file system)
    Swap          2 GB

and then install the boot loader... somewhere.

Questions:

1.) This:

[ATTACH=CONFIG]286437[/ATTACH]

 is what I see when I try installing Ubuntu with my 6 HDDs removed from my motherboard and just the two connected in RAID 1 to the PCI RAID controller card. Which partition do I use to create the required partitions?

2.) Where do I install the boot loader without nuking my W10 install?

Here are the screenshots of the "Installation Type" screen with all HDDs inserted:


[ATTACH=CONFIG]286434[/ATTACH][ATTACH=CONFIG]286435[/ATTACH]

---

### Post by Shmoogly on 2020-07-13
Well, according to this web page: [https://neosmart.net/wiki/easybcd/uefi/?utm_source=EasyBCD&utm_medium=software&utm_campaign=EasyBCD%20EFI](https://neosmart.net/wiki/easybcd/uefi/?utm_source=EasyBCD&utm_medium=software&utm_campaign=EasyBCD%20EFI) it looks like it's impossible for me to create a dual boot system :(.

---

### Post by ActionParsnip on 2020-07-13
You can, just disable secure boot and install Windows then install Ubuntu

---

### Post by Shmoogly on 2020-07-13
Bummer, it took quite some time to install W10 with all my programs. Looks like I'm stuck with using a VM for linux. Oh well, at least that means I can alt tab between OSs, also not the worst.

---

### Post by Shmoogly on 2020-07-14
> **ActionParsnip said:**
> You can, just disable secure boot and install Windows then install Ubuntu

Actually, your point has made me think... I didn't buy the computer with W10 pre-installed. I installed W7 myself and then updated to W10. Does this change anything?

---

### Post by mastablasta on 2020-07-14
add USB as boot device boot, then add just the boot loader on it and boot all systems from it.

also why does windows have 6 SATA drives? any particular reason for that? What if you moved 4 of those on controller and move 2 linux drives on motherboard?

---

### Post by Shmoogly on 2020-07-14
I was wondering whether it's possible to boot off a USB, I will look into it!

x2 SSD drives in RAID 1 for Win10, x4 spinny disks in RAID 10 for all the data/programs etc. So I don't think I can move as per your suggestion. Not without re-installing Windows since my programs are installed on the RAID 10 drive.

---

### Post by Shmoogly on 2020-07-19
I just realised something. I turned on my computer and this is what I saw:

[ATTACH=CONFIG]286490[/ATTACH]

This is with no USBs plugged into my computer, so obviously, I have remnants of my old Ubuntu install still on there. Is there any way to find out which partition that Grub boot loader is installed on? Is it possible to install a fresh Ubuntu and Grub boot loader over the top of the old one?

If I boot into ubuntu, I see grub:

[ATTACH=CONFIG]286491[/ATTACH]

Or perhaps it might be possible to install Ubuntu from a USB and then link Grub to the new Ubuntu instance?

---

### Post by CelticWarrior on 2020-07-19
All bootloaders in a UEFI system reside in the ESP (EFI System Partition) and they persist even when the any given OS' system's partition is removed. Not a problem. "Orphaned" bootloaders do nothing except wasting a few megas of space in the ESP that should be big enough to store a lot more.

There are tools to clean up those remnants in Windows and Ubuntu but you can just reinstall Ubuntu if you want. Worst case scenario you'll end up with duplicated Ubuntu bootloaders, one that works and other, the old one, that doesn't. The old entry can be easily removed with efibootmgr later.

---

### Post by mastablasta on 2020-07-21
> **Shmoogly said:**
> I was wondering whether it's possible to boot off a USB, I will look into it!


you can also boot from a floppy disk, if you want to. : [https://www.plop.at/en/bootmanagers.html](https://www.plop.at/en/bootmanagers.html)

i used plop on old machine to boot linux live image from floppy disk. the old PC doesn't recognise new USB keys where the live image was "burned".

---

### Post by Shmoogly on 2020-08-02
Well I installed Ubuntu with the bootloader pointed to a USB memory stick. Everything went fine with the install. However I can't boot into Linux. I see this screen if I boot off the memory stick. What next?

---

