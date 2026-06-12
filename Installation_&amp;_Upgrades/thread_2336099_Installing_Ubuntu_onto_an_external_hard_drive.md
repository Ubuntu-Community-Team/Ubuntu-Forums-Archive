---
title: "Installing Ubuntu onto an external hard drive"
date: 2016-09-04
forum: Installation &amp; Upgrades
---

### Post by Sonofagun72 on 2016-09-04
I'm trying to install Ubuntu onto a portable USB 3.0 1 TB hard drive. I want to be able to boot off of the hard drive when it's plugged in to a computer and run Ubuntu solely off of it. I've tried multiple times and was able to successfully install Ubuntu but couldn't get the hard drive itself to boot. 
I am using a 32 gb flash drive with a Ubuntu installer on it and I am able to boot from it, try Ubuntu, and launcher the installer. I start the installer and chose "Something else" in the installation page, then I set up two partitions on my drive, an 800 gb ext4 partition for Ubuntu with the mount point the root "/". The next is 12 gb swap partition. And the other ~188gb as free space. The bootloader is also set for the root of the external drive. The installer will run through and complete. However after when I finally try to boot from it. My bios won't recognize it as a bootable device. USB booting is enabled in my bios and I've tried a few computers and it won't show up in the boot options. But other usbs like the Ubuntu installer will show up. So I'm pretty much lost as what to do. I've experimented with so many different partition types and nothing works. I see on the external drive the Ubuntu files are all there but I can not boot it. I'm pretty sure the issue has to be something with the bootloader since the installation goes smoothly. I've tried searching the forums and it seems like there shouldn't be an issue. Thanks.

---

### Post by ubfan1 on 2016-09-04
If you are trying to boot in UEFI mode, you should put an EFI partition (300M, FAT fs) partition on the external, then copy the internal disk's EFI partition to the external EFI.  Then copy grubx64.efi and shimx64.efi from the external's /EFI/ubuntu to /EFI/Boot, then rename /EFI/Boot/shimx4.efi to /EFI/Boot/bootx64.efi.

---

### Post by Sonofagun72 on 2016-09-04
> **ubfan1 said:**
> If you are trying to boot in UEFI mode, you should put an EFI partition (300M, FAT fs) partition on the external, then copy the internal disk's EFI partition to the external EFI.  Then copy grubx64.efi and shimx64.efi from the external's /EFI/ubuntu to /EFI/Boot, then rename /EFI/Boot/shimx4.efi to /EFI/Boot/bootx64.efi.

Could you elaborate more on the efi partition? I have one on the external drive. My external has a ext4, swap, and efi partition. How to I access the efi partition on the ubuntu usb trial, since it doesn't show up in file manager, but does in gparted? Also what do you mean by internal drive? If you mean the internal drive of the computer, well its a windows 10 os on the internal drive so I dont know how the internal's drive efi related to that then. Also I'm confused on what you mean by "/EFI/ubuntu", on the root of the drive "/" there is no efi folder, its just the ubuntu os files like "bin,boot,dev,etc,home, and so on. From /boot there is an efi folder and grub folder, not sure if this is what you mean.

---

### Post by Dennis N on 2016-09-04
> The bootloader is also set for the root of the external drive.

This is part of the problem. I will take the liberty of offering this bit of information: When you do a UEFI install of Ubuntu, the grub boot loader installs only to the EFI system partiton of your primary drive (sda) regardless of what you specify during the installation. A boot directly to sdb is not possible without a further fix. 

With the usb connected, are you able to boot Ubuntu by booting to sda - either through the UEFI boot manager or through grub? I think there would be Ubuntu boot files installed in the EFI system partition of sda. 

I have never done a UEFI install to a portable USB drive, but ubfan1's advice is what I have read needs to be done to boot directly from sdb in UEFI mode. I will defer to him or others for further assistance in carrying out those steps, since I haven't done this myself.

---

### Post by Sonofagun72 on 2016-09-04
Just to clarify there are 2 usb's in the scenario, one is the external hard drive usb, and one is a flash drive usb with the ubuntu installer. The flash drive will boot into the grub bootloader which then lists try ubuntu, install ubuntu, etc. So I'm assuming your asking if I can boot into ubuntu on the external while the other flash drive is installed? If that's the question then no it still takes me to the grub bootloader which give me the options to try ubuntu, install ubuntu, oem install, check disc for defects.

---

### Post by Dennis N on 2016-09-04
> I've tried multiple times and was able to successfully install Ubuntu but couldn't get the hard drive itself to boot. 

I gather from the above that you went through the "Install Ubuntu" process in the installer and it completed the installation. Then you must have rebooted to see if it works. You should have been prompted to first remove the usb installer before it reboots. You don't want the installer plugged in when the system reboots (or later starts up). After the reboot, let it boot normally - my question rephrased: (with installer unplugged) do you see a grub menu or does it boot into Windows? 

I also assumed you want this install to the 1 TB drive to be portable to another computer? That is the reason for moving of boot files that ubfan1 talks about - so that they are on the drive with the OS as it is used elsewhere.

---

### Post by Sonofagun72 on 2016-09-04
So when I reboot after the install, and remove the flash drive, it boots into windows boot manager and boots up windows 10. If I boot into bios and manually choose where to startup from it will not show the external drive as an option.

---

### Post by ubfan1 on 2016-09-05
If gparted shows an EFI partition on your USB drive, (type c for fat32), then you need to put a fat filesystem onto it.  From the live system, run mkdosfs /dev/sdb3   or whatever your disk and efi partition is (maybe it's sdc instead of sdb if you are booting off your install usb. check that the partition is 3 for the efi too).  Then make a directory in /tmp to mount it.  mkdir /tmp/efi   and sudo mount -tvfat /dev/sdb3 /tmp/efi .   Now can make another directory in /tmp for the internal disk's efi (e.g. /tmp/internalefi) and mount it  sudo mount -tvfat /dev/sda?  /tmp/internalefi.  Now you may just copy everything seen in /tmp/internalefi to /tmp/efi.  sudo cp -a /tmp/internalefi /tmp/efi   I think that is the first step to getting the bootloaders onto the external disk.  Then you need to copy the bootloaders into the default location for removable media:  sudo cp /tmp/efi/EFI/ubuntu/grubx64.efi /tmp/efi/EFI/Boot/grubx64.efi    and  sudo cp /tmp/efi/EFI/ubuntu/shimx64.efi /tmp/efi/EFI/Boot/bootx64.efi    (not the name change in the copy).  Assuming the orignal install did set up the internal disk's .../EFI/ubuntu directory, that should boot in UEFI mode. All that assumes you are in UEFI mode.

---

### Post by Dennis N on 2016-09-05
> **Sonofagun72 said:**
> So when I reboot after the install, and remove the flash drive, it boots into windows boot manager and boots up windows 10. If I boot into bios and manually choose where to startup from it will not show the external drive as an option.

OK that helps all to understand how the system is behaving. Before, you were booting back into the installer. 

With Windows, there are problems of "my system boots directly to Windows" instead of a grub menu. Yours sounds like it might be such a problem. I'm not up on fixes to Windows dual booting problems - some are specific to the brand of computer you are using. But there are a couple of guys here who know details, and this is the right section to post in.

---

### Post by sudodus on 2016-09-05
We are rather sure that your computer is running in UEFI mode. You can boot from the USB pendrive with an Ubuntu live drive (the Ubuntu installer drive). Then you can also boot (in the same way) for a USB hard disk drive with the correct boot configuration.

I made an installed system, that can boot from UEFI as well as from BIOS. If you install it with ***mkusb*** or ***Win32 Disk Imager*** from a compressed image file, you will get the correct boot configuration automatically. See this link,

[Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

-o-

Another alternative is to remove your internal drive. Then the external hard disk drive will be /dev/sda, and you can install Ubuntu into it with a correct EFI partition, and you get an external system that boots in UEFI mode (but not in BIOS mode).

After the installation you plug in your internal drive again, and the external hard disk drive should be bootable (via the same method as your USB pendrive).

---

