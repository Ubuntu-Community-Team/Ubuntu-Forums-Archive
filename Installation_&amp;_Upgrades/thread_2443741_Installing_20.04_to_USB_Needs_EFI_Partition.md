---
title: "Installing 20.04 to USB: Needs EFI Partition"
date: 2020-05-19
forum: Installation &amp; Upgrades
---

### Post by bilkay on 2020-05-19
I wanted to install 20.04 onto a USB thumbdrive (worked with 16.04). The installation stopped with a message that the thumbdrive (the same one I installed 16.04 on) needed an EFI partition. I wish I knew how to add one. The "best" solution I could come up with was using the Windows diskpart utility, but when I tried it, it made the entire disk an EFI partition and gparted says it's ext4. Everything I've read says it should be FAT32.

I'm wondering why the 20.04 installation doesn't make the partition instead of just stopping and leaving me hanging.

---

### Post by yancek on 2020-05-19
I would start by reading the Ubuntu documentation at the link below.  Some of it deal w/dual booting w/windows but other parts of it are specific to UEFI/GPT.  Check is your usb is GPT and you can use GParted which is on the Ubuntu install usb to create partitions.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

> I'm wondering why the 20.04 installation doesn't make the partition instead of just stopping and leaving me hanging. 		 

You are using the manual install method (Something Else) correct?  Do you have another OS installed on the computer and if so, what?

---

### Post by oldfred on 2020-05-19
Ubuntu's Ubiquity installer wants to only install grub to first drive, usually your internal drive.
The error message may be because you do not have an ESP - efi system partition on internal drive?

If not installing to first drive, you need to partition in advance, I use gparted and use 100 to 500MB for ESP. If really small flash drive I might use just 50GB, since only Ubuntu's grub files will be in it. And then rest as ext4 for / (root).

But to get Ubiquity to install to correct ESP, I have to trick it during install.
Posted work around to manually unmount & mount correct ESP during install #23 & #26
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

Many find it easier to just unplug all drives, but that cannot be done in all cases. Newer UEFI systems have settings to disable a drive which is the same as unplugging it and that also can work. Then default install will create ESP & / on the one drive you are installing into.
I also have created ESP on flash drive and just copied all of /EFI/Boot & /EFI/ubuntu to external drive and edited fstab with correct UUID for external drive's ESP.

---

### Post by bilkay on 2020-05-20
The new PC came with no OS installed. I used gparted to add a 200MB fat32 bootable partition before the main partition on the thumbdrive, labeled it "EFI" and the installation went smoothly. It was actually easier than the jargon-infused how-tos led me to believe. It just seemed that it was something the installer could have handled.

Thanks for the responses!

---

### Post by C.S.Cameron on 2020-05-20
While you are creating a Full install USB that boots in UEFI mode might as well make it bootable in BIOS mode also: 
[https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step](https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step)

---

