---
title: "Which partition for boot loader?"
date: 2015-10-18
forum: Installation &amp; Upgrades
---

### Post by 4UwgKA83Ui on 2015-10-18
Hello everyone!

So, I've been studying how to install Ubuntu on a machine with Windows 8.1 already installed (and therefore with UEFI). All the tutorials show more or less the same procedure, but in [this one]("https://youtu.be/46FtBpv6Bjk?t=13m10s") the boot loader is installed in the same partition as the root partition. From what little I understood, this is important so that the windows grub doesn't overwrite or change the ubuntu one.
However I haven't seen this procedure in any of the other tutorials. What difference does it really make? Is it something you would recommend? 

Thanks! :p

---

### Post by Dennis N on 2015-10-18
If the computer has only one HDD, in a UEFI installation, Ubuntu will always install the boot loader in the first EFI system partition on your disk - other location choices are ignored. If there are two or more hard drives, Ubuntu's current installer will install a boot loader in the first EFI system partition of the first SATA drive, even if you make another selection.

---

### Post by 4UwgKA83Ui on 2015-10-18
Thank you for your quick reply!
So if my laptop has only one HDD and it's SATA, changing its location won't really matter?
And is it true that installing the boot loader in a different partition will ensure less issues with booting?

---

### Post by Dennis N on 2015-10-18
> **Renee_Montoya said:**
> Thank you for your quick reply!
So if my laptop has only one HDD and it's SATA, changing its location won't really matter?
And is it true that installing the boot loader in a different partition will ensure less issues with booting?

The boot loader must be installed to an EFI system partition if you are installing in UEFI mode. The installer appears to give you a choice of where to install it, but they don't work. The installer always uses the first EFI system partition it can detect on your disk drives, starting with sda. 

This is peculiar to Ubuntu's installer program (called Ubiquity). Other Linux (Fedora, Open Suse, Manjaro, etc) will install to the EFI system partition that you designate.

---

### Post by Dennis N on 2015-10-18
Just to be clear, since your Windows 8.1 has created and is using an EFI system partition already, Ubuntu will find and install it's boot loader on the same one. They will happily coexist there. Nothing to worry about.

---

### Post by 4UwgKA83Ui on 2015-10-18
Oh, ok! Now I understand better!
Thanks! :p

---

### Post by oldfred on 2015-10-18
Example shown was a BIOS install also. 

And even then you normally do not install grub to a partition. A few users prefer using Neosmart's solution with BIOS and primarily booting Windows, but that is not recommended. It still uses its own grub4dos and its own boot to chainload to the grub in the partition boot sector. But grub2 does not fully fit into a partition boot sector and uses blocklists or hard coded addresses which are not reliable.

With UEFI grub always installs to the ESP - efi system partition on sda. And you can only have one ESP per device.

---

### Post by Dennis N on 2015-10-18
> With UEFI grub always installs to the ESP - efi system partition on sda. And you can only have one ESP per device.

This is true for Ubiquity (current version), but if we allow other Linux distros in, you can have several ESPs on one device.

Here is the setup I have on my Zotac, with two ESP partitions. Unnamed partition #6 is a shared data partition. Ubuntu MATE, Mint MATE and Manjaro use ESP partition #1. Fedora uses ESP partition #8. Both Fedora and Manjaro installers allowed selection of the ESP partition (including which drive, if more than one drive), which I really wish Ubuntu would do.

```
[dmn@Zotac ~]$ sudo gdisk -l /dev/sda
[sudo] password for dmn: 
GPT fdisk (gdisk) version 1.0.0

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 488397168 sectors, 232.9 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 9BA11D12-7A3E-4D56-AD22-50D56810D3E2
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 488397134
Partitions will be aligned on 2048-sector boundaries
Total free space is 123521325 sectors (58.9 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          165887   80.0 MiB    EF00  EFI System Partition
   2          165888          169983   2.0 MiB     EF02  
   3          169984        45225983   21.5 GiB    8300  Ubuntu-Mate
   4        45225984        53417983   3.9 GiB     8200  
   5        53417984       114857983   29.3 GiB    8300  Mint-Mate
   6       114857984       278697983   78.1 GiB    8300  
   7       278697984       319657983   19.5 GiB    8300  Manjaro-XFCE
   8       319657984       319821823   80.0 MiB    EF00  EFI System Partition
   9       319821824       364877823   21.5 GiB    8300  Fedora

```

---

### Post by oldfred on 2015-10-18
I know UEFI is supposed to allow multiple ESPs, but I thought it was UEFI that was the issue.

I also know that Ubuntu/grub only installs to sda. I install another copy to sdb, during install it says installing grub to sdb, and it overwrites the grub.cfg in my sda's ESP.

---

