---
title: "Dualboot Partitioning with 2 hard drives"
date: 2016-11-19
forum: Installation &amp; Upgrades
---

### Post by doopy2 on 2016-11-19
Hey guys,

I'm trying to setup a system with both Windows 10 and Ubuntu. Currently I have only a fresh installed Windows 10.
Also, I have 2 internal hard drives, one SSD only for Windows and one (currently empty) 2 TB HDD for Windows data/programs and now also Ubuntu.
I'm planning to give 300GB to the Ubuntu partition, I hope that will be enough.

Can I use that drive for both Windows programs and Linux? If yes, what program should I use for partitioning? Windows' diskmanager, or the one that comes with the Ubuntu installer, or even a third party program?
Also, how exactly should I partition? As far as I know, Ubuntu uses even a different file system, currently the drive is formatted with NTFS. I'm pretty much an amateur when it comes to formatting/partitioning.

Thanks for any help in advance!

---

### Post by oldfred on 2016-11-19
Is system UEFI or BIOS and then if UEFI partitioning must be gpt.
Only use Windows to shrink NTFS partitions. And reboot immediately and run chkdsk on the NTFS partition. If boot partition, it may auto run chkdsk.

Then use gparted to create partitions in advance and use Something Else as install option. Or you can create partitions with installer.
But with installs to second drives you want grub2's boot loader on second drive if system is BIOS. If UEFI grub will only install to the ESP - efi system partition on sda which will be shared with Windows boot files.

Default install is / (root) and swap. And for newer users that is all you need. 
Bit more advanced is adding another partition for /home and keeping / smaller like only 25GB. 
Then what I use is a large data partition and keep /home inside my /. Back with Windows my data partition originally was NTFS, then as I phased out Windows NTFS data partition was used less & less & the ext4 data partition became my main data store.

       [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) 
            Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)

---

### Post by doopy2 on 2016-11-20
Thanks for your answer!
First of all, Windows is installed in UEFI Mode.
However, I did install ubuntu already before your post. I booted from my USB stick in UEFI mode, and created 4 partitions, root, home, swap and an EFI partition, all on the second hard drive.
Now I have the problem, that I can't boot from ubuntu, but the OS seems to be installed, I can find all partitions and system folders via live usb stick.
If I understood that correctly, according to your post the EFI partition should be on my SSD with Windows together? Or shouldn't I have created an EFI partition at all, but select the EFI partition of Windows?
 Is it still possible to change that now?

---

### Post by doopy2 on 2016-11-20
So I tried to reinstall grub, but since that got very complicated I just decided to reinstall ubuntu completely. 
In my first installation, in the partition manager of the ubuntu installer, I chose my EFI partition as 'device for boot loader instructions', according to a German tutorial I followed.
However, in my second try I chose the second harddrive (sdb), according to oldfred's link: [https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
After installation and rebooting I got into the grub boot selection window, and everything works now.
Thanks a lot!

EDIT: I'd still like to hear an explanation why one has to choose this or that device (drive/partition) in order to make it work. Why is the boot stuff not found when it's in the EFI partition?

---

### Post by oldfred on 2016-11-20
It should not have mattered what you chose with UEFI installer, although always best to choose correct drive as someday they will fix it (hopefully).
 
The UEFI installer only installs grub's boot files to the ESP - efi system partition on the drive seen as sda. I just did a full install to a flash drive, choose that drive sdc as drive to install boot loader and it overwrite my main working installs /EFI/ubuntu folder in sda. I had backed up or done this enough times, that I knew how to quickly restore from backup, but for most it could be a big issue.

I always suggest each drive be bootable without any other drive. Difficult with UEFI. But still have an ESP on your Ubuntu drive, even if not currently used. And I might copy boot files/folders from ESP on sda to ESP on Ubuntu drive. Both as backup and possibly a way to boot, but you probably would still need a repair/installer flash drive to run commands to use it.

---

