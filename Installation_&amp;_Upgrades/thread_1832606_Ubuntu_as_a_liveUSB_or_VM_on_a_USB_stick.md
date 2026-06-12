---
title: "Ubuntu as a liveUSB or VM on a USB stick?"
date: 2011-08-25
forum: Installation &amp; Upgrades
---

### Post by Jerry_03 on 2011-08-25
Hi all, I dont really use ubuntu too much, just for my programming class. Anyways I want to have ubuntu on a USB stick so I can use it on my laptop, netbook, desktop PC at home and desktop PC in class, all of which run Windows natively.

I would prefer the Virtual Machine (VM) on a USB stick but im not sure if its possible to install virtualbox (my VM of choice) on a USB drive. if not then a liveUSB, though correct me if im wrong but would i be able to save files on a liveusb?

If I do go with the VM on the usb stick option, i need an idea what size USB stick to buy so what is the bare minimum space you can run ubuntu on? I also intend to run OpenSUSE which is why i prefer the portable vm option.

Thanks.

---

### Post by lmarmisa on 2011-08-25
My solution for a problem similar to yours was to use a 2.5'' external USB 2.0 hard drive. This kind of devices does not require any AC power adapter. Its weight is only 160 gr (0.35 pound).

I defined some partitions in that hard drive ( I used an Ubuntu Live CD for that purpose):
[INDENT] 1) A 15 GB ext4 partition for Ubuntu (root /).

2) A 4 GB swap partition.

3) A big 480 GB NTFS partition for data.
[/INDENT]Then I installed Ubuntu in that external hard drive. During the installation, I selected manual partitioning and installed the GRUB loader in the [Master Boot Record ]("http://en.wikipedia.org/wiki/Master_boot_record")of the external hard drive. This is a portable operating system that runs in several computers. Therefore, I have not installed any proprietary drivers.

This Ubuntu system runs fine in many computers. Anyway, you will need that the BIOS of the different computers supports the boot from USB device option.

---

