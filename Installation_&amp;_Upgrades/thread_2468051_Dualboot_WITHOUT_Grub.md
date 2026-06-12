---
title: "Dualboot WITHOUT Grub??"
date: 2021-10-17
forum: Installation &amp; Upgrades
---

### Post by zamfp on 2021-10-17
Hi there :)

I want to install Ubuntu 21.10 *without* the installer installing Grub. I currently have Windows 11 on a 2TB SSD and want to install Ubuntu for testing on a 240GB SSD.

I want to be able to select my OS via the BIOS (UEFI) boot selection tool. 

I don't want any dramas if I decide to get rid of Ubuntu, which is why no GRUB!

Cheers :)

---

### Post by tea for one on 2021-10-17
Your intention to keep Ubuntu and Windows 11 separate is a sound choice.
Here is a little check list:-

De-activate, disconnect, isolate or physically remove existing Windows OS drive so that only the target drive is accessible
Boot Ubuntu live and check that you are in UEFI mode
Open a terminal and enter:-
```
[ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy"
```
Create GPT on your target disk using gparted
Open gparted > Device > Create Partition Table > Select gpt
Allow the installer to automatically create the necessary partitions (or your preferred configuration)
Double check that an EFI partition will be created
Boot each system independently via UEFI boot screen (ideal not cumbersome)
Boot priority can be controlled by UEFI
Each OS should be installed in UEFI mode with GPT
Each drive should have EFI partition
Each drive should have boot manager (Windows Boot Manager and Grub for Ubuntu)
De-activate, disconnect, isolate or physically remove one drive so that you can check if the other boots independently (and vice versa)

Grub will be installed otherwise you would not be able to boot Ubuntu.
You will have to be vigilant with updates (especially grub updates).
If your Windows drive is visible during a kernel or grub update, then it will probably take control of the boot process for both systems.

---

### Post by zamfp on 2021-10-17
Thanks for the reply.

I cannot disconnect the drive as it's NVME and I'm not comfortable removing it. Any other options??

Thanks

---

### Post by tea for one on 2021-10-17
You may be able to de-activate the nvme Windows drive in your UEFI settings.

Device > PCI (or similar as attachment)

---

### Post by zamfp on 2021-10-17
Thanks for your help! I looked and there is no setting there, unfortunately :(

---

### Post by Impavidus on 2021-10-17
Can the Windows drive be disabled in UEFI? That should work. Otherwise, grub will be installed on the EFI partition of the Windows drive, even if you select the Ubuntu drive for that. It's considered a bug. It's not too bad though. Back in the BIOS days, installing one bootloader would overwrite the other, but with UEFI multiple bootloaders can be together in one EFI partition. When you remove Ubuntu, just switch back to the Windows bootloader.

---

### Post by zamfp on 2021-10-17
> **Impavidus said:**
> Can the Windows drive be disabled in UEFI? That should work. Otherwise, grub will be installed on the EFI partition of the Windows drive, even if you select the Ubuntu drive for that. It's considered a bug. It's not too bad though. Back in the BIOS days, installing one bootloader would overwrite the other, but with UEFI multiple bootloaders can be together in one EFI partition. When you remove Ubuntu, just switch back to the Windows bootloader.

Thanks. That would not be a problem (the GRUB installation behaviour), but, I have had trouble in the past removing GRUB and don't want it to happen again, if possible.

---

### Post by grahammechanical on 2021-10-17
You say that in the past you have had trouble with Grub when you removed Ubuntu. Was this is the days of BIOS motherboards? In those days a person needed to re-install the Windows boot loader.

I do not own a UEFI motherboard computer but I understand that with UEFI the Windows boot files are not overwritten. As stated by Impavidus there is space in the EFI partition for multiple bootloaders and they coexist peacefully. It is certainly a long time since anyone came on this forum and said that they removed Ubuntu and now Windows won't load. Things changed with UEFI and Windows 8 onwards.

There is one thing that hasn't changed. Windows bootloaders still do not recognise the existence of other operating systems. So, without a Linux bootloader (Grub) you will not be able to load Ubuntu.

Regards

---

### Post by oldfred on 2021-10-17
You can manually install Ubuntu in UEFI boot mode to any second drive, but have to manually gpt partition to include an ESP on second drive and do one of several work arounds. 
Ubuntu's Ubiquity installer will only install grub to first drive's ESP. That works fine for one drive or even a second internal drive if second drive always used with same system.
Just found a page where Apple automatically adds an ESP to every drive as first partition. I have done that since converting to gpt & UEFI.

Oldfred's workaround during install.
Posted work around to manually unmount & mount correct ESP during install #55 or( #23 & #26)
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall of grub to correct drive. 

Remove esp flag from Windows before install to second or external drive - Tim Richardson (Also in bug report as workaround)
Be sure to add ESP flag back to Windows drive's ESP after Ubuntu install.
[https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator)

UEFI/gpt partitioning in Advance, new versions use swap file so swap partition optional:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu) 

You can also use gparted but must change device label or default partitioning first.
With gparted select gpt under device, advanced over msdos(MBR) default partitioning before starting.
300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another) as first partition.
30+ GB Mountpoint / (root) as ext4
Remaining part of drive /home as ext4
4 GB Mountpoint swap (optional as default now is swap file) If swap partition put at end of drive.

---

### Post by Dennis N on 2021-10-17
If one drive is NVMe, and the other SATA, then I believe the boot loader location selector will work. The installer default for installing grub now is the ESP of an NVMe drive if there is one, but I do recall choosing the ESP on the SATA drive (which is sda1) as my choice and it was used for this installation. See below: root partition is on a logical volume on the NVMe, and ESP on sda1. (I could have installed root on sda as well, as the OP plans to do, but lose the speedy access.)
```

dmn@Sydney:~$ space
Filesystem                        Size  Used Avail Use% Mounted on
udev                              5.8G     0  5.8G   0% /dev
tmpfs                             1.2G  1.9M  1.2G   1% /run
[COLOR="#FF0000"]/dev/mapper/sn500_vg-ubuntu_1804   26G   23G  2.1G  92% /[/COLOR]
tmpfs                             5.8G     0  5.8G   0% /dev/shm
tmpfs                             5.0M  4.0K  5.0M   1% /run/lock
tmpfs                             5.8G     0  5.8G   0% /sys/fs/cgroup
/dev/mapper/os_vg2-Common          85G   48G   33G  60% /mnt/Common-Files
/dev/mapper/sn500_vg-vm_disks     183G  107G   68G  62% /mnt/VM-Disks2
[COLOR="#FF0000"]/dev/sda1                          79M   25M   55M  31% /boot/efi[/COLOR]
tmpfs                             1.2G   24K  1.2G   1% /run/user/1000

```

---

