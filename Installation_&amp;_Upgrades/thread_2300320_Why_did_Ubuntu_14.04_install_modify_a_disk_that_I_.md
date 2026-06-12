---
title: "Why did Ubuntu 14.04 install modify a disk that I did not select during install?"
date: 2015-10-25
forum: Installation &amp; Upgrades
---

### Post by jamin2 on 2015-10-25
I have a Dell XPS 13 with Windows 8.1.  I wanted to install Ubuntu 14.04 on a USB drive and set up the BIOS to Boot from USB first.  My Goal was to boot into Windows without the USB drive, and boot into Ubuntu, when I had the USB drive inserted.  I thought this would be easy, but it wasn't.

I booted to another USB drive that had a pendrive Ubuntu installer on it, and proceeded to install linux on the blank USB drive.  During install, I made 3 partitions on the USB drive.  1 efi, 1 ext4 (mount point for /), and 1 swap space partition.  I spent some time making sure that the Install was targeting the USB drive.  So I finish the install, and apparently the installer went to the MBR on the NTFS drives and added a grub boot point.  Now when I take out the USB drive, the grub screen just hangs and will not allow the computer to boot into windows.

Looking in my boot options in the BIOS, there is an ubuntu option pointing at the NTFS drive.  The only way to boot windows is to lower the priority of the Ubuntu boot.  

What I really want is to insert a USB, and have the BIOS recognize it as UEFI bootable, and boot into linux if the USB drive is present.  And if the USB drive is not present boot into Windows 8.1

I'm actually upset that Ubuntu did not warn me that it was going to modify the NTFS SSD.  I did not think the install would touch the SSD.  I am not sure why this happened,   Also, my efi partition seems to be perfectly available in ubuntu, but the swap space is inaccessible.  I turned on the  Secure Boot option, but then Ubuntu did not boot when that was enabled.  I thought that it might work, since the shimx64.efi file was in the Win 8.1 OS efi partition.

So my question is, Do i need an EFI partition on the USB Drive, and if so, how  do i set up a proper boot point to the USB drive

---

### Post by sudodus on 2015-10-25
Welcome to the Ubuntu Forums :-)

The best way to do what you want is to remove the internal drive, and install Ubuntu into the USB drive.

When you install Ubuntu using some of the automatic methods, it will install the bootloader into the first drive, and it happens to be the internal drive with Windows. The installer is made like that (by design). We may like it or not.

- I always recommend to ***backup*** everything important before the installation, because it is risky.
- I usually recommend to ***remove the internal drive*** before the installation to a separate drive (internal or external).

But there is also another way to do it. You can select ***'Something else'*** at the partitioning window of the installer. Then you can select partitions (or create partitions) where to install Ubuntu. And ***at the bottom of the window you can select where to install the bootloader***. Select the head of the drive, **/dev/sda** for the first drive, **/dev/sdb** for the second drive etc. There should ***not*** be a partition number (except in very special cases). In your case you would probably select **/dev/sdb** or **/dev/sdc**, depending of the order your pendrive and USB HDD are mounted.

-o-

But now you have the acute problem to re-install the Windows bootloader into the internal drive. You need Windows tools to do that. You can find many tutorials via the internet how to do it, and with a little bit of luck, you will get detailed help here :-) [COLOR="#696969"](I'm no longer good at repairing Windows, but several users here know.)[/COLOR]

---

### Post by oldfred on 2015-10-25
External drives boot from /EFI/Boot/bootx64.efi and it must be in the ESP - efi system partition. So yes you need the efi partition on external drive, FAT32 with boot flag.

But grub installer does not create that file, you have to manually create it. Grub installed to the ESP on sda as /EFI/ubuntu. If booted into Ubuntu it will be mounted at /boot/efi or full path /boot/efi/EFI/ubuntu
You need to copy that from sda to sdb's efi partition as /EFI/ubuntu and then copy again to /EFI/Boot. Then rename shimx64.efi to bootx64.efi.
Then your UEFI should see an UEFI bootable external device.

I have installed to a internal sdb drive and external flash drives as full installs. And it does say installing to sdb, but overwrites my /EFI/ubuntu in sda every time. :(

From Ubuntu you can also do a grub install with the removable option and it will create correct grub to sdb, but it still needs you to manually create the grub.cfg (I think). I need to try that.

---

