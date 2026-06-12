---
title: "Challenging question: install Linux with no floppy, USB or CD drive"
date: 2008-08-16
forum: Installation &amp; Upgrades
---

### Post by pytheas22 on 2008-08-16
This question pertains to Damn Small Linux, not Ubuntu, but I thought it would be best to post it here because there's no DSL section in the "Other OS Discussion" category.

I have a really old machine (Pentium I/32 MB) on which I want to put DSL.  Unfortunately it has no working floppy, CD or USB device, and because it's an old laptop, I have no way of moving its hard drive to another computer.

The machine does have a working FAT32 hard disk with Windows 95 installed, and a working ethernet interface (I can't boot to network, however).  So I downloaded the DSL .iso and extracted it on the Windows system.

I'm thinking that I can make the system boot to DSL along the same lines as wubi.  I know that wubi creates a disk image at c:\ubuntu\disks\root.disk and installs Ubuntu inside it.  But I don't know enough about how wubi works or the Windows 95 bootloader (which apparently is quite different than the NT bootloader) to know 1) how to make the disk image; 2) how to put the DSL files inside the disk image properly; or 3) how to edit the Windows bootloader so that it will boot to DSL.

I'd be grateful for suggestions on how to accomplish the above three steps, or for other approaches I might take to solve the problem--I've thought about trying to install grub on the system or shrinking the Windows partition to give DSL its own partition (which I guess would also require grub to boot), but I'm not sure it's possible to do those things without a live CD.  I did manage to install UNetbootin, which allows me to boot (via the Windows bootloader) to the equivalent of Super Grub Boot Disk, but I so far haven't been able to find a way to do anything useful with it.

---

### Post by Partyboi2 on 2008-08-16
> I did manage to install UNetbootin, which allows me to boot (via the Windows bootloader) to the equivalent of Super Grub Boot Disk, but I so far haven't been able to find a way to do anything useful with it.
You should be able to select "Darn Small Linux" for the "Distribution" option and then down then bottom for "type" choose "hard disk" not "usb drive" then when you press ok it should download , extract, copy, install the boot loader then ask you to reboot. Once it reboots and you select unetbootin it should load up darn small linux where you will see a open window called "getting started with dsl" where you can select "installing from hard drive" which will give you info on installing to your hard drive.

---

### Post by pytheas22 on 2008-08-17
Thanks, that worked quite well (at least in my virtual environment; I'll try it with the real thing later).  I think that the version of UNetbootin that I originally used only allowed me to install Super Grub Boot Disk, not any distribution.  I downloaded the version of UNetbootin from the project's sourceforge site and it works very well; it should be much easier than I anticipated to get DSL installed.  Thanks again.

---

