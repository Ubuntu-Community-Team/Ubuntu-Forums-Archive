---
title: "Reset Windows and Now Ubuntu Loads Into Minimal Bash Like Line Editing"
date: 2022-11-04
forum: Installation &amp; Upgrades
---

### Post by chrisg-32 on 2022-11-04
I have a Dell laptop that I dual boot Windows 11 and Ubuntu 20.04 LTS from the same SSD with. Recently, I reset Windows and after doing so Ubuntu gave me that error. I have tried using Boot Repair and doing it manually as detailed on [https://www.linuxfordevices.com/tutorials/ubuntu/fixed-minimal-bash-like-line-editing-is-supported-error](https://www.linuxfordevices.com/tutorials/ubuntu/fixed-minimal-bash-like-line-editing-is-supported-error) but I have had no luck. Specifically on the EFI partition of my drive /mnt/boot/efi didn't exist when i tried to mount it there. Here is the pastebin from boot repair [https://paste.ubuntu.com/p/X2BJsrxqdn/](https://paste.ubuntu.com/p/X2BJsrxqdn/). Secure Boot is off and this may be important but the space where Ubuntu was was marked as unallocated until I formatted it as ext4 thinking this would fix the issue. Windows disk management says it is a healthy Primary Partition if this helps. Ideally I would like to not just reinstall Ubuntu as I'm fairly sure the information for the OS is still in that part of the hard drive. When I installed Ubuntu originally I installed alongside windows boot manager which may also be important.

---

### Post by oldfred on 2022-11-04
While p6 says Linux, the report showed none of the files it normally shows from a Linux install.
It might first try fsck on nvme0n1p6.

```
To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required, Run both commands as they have different parameters.
sudo e2fsck -C0 -p -f -v /dev/nvme0n1p6
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/nvme0n1p6


```

Post back if any errors.

Then I would see if Boot-Repair  correctly sees your install.
And/or use advanced mode to totally reinstall grub and latest kernel.

---

### Post by tea for one on 2022-11-04
Boot-repair has only detected one operating system Windows 10 or 11 (Lines 73 - 75)
> **chrisg-32 said:**
> the space where Ubuntu was was marked as unallocated until I formatted it as ext4 thinking this would fix the issue
It appears that you have obliterated Ubuntu by re-formatting.

Do you have personal data backups of both Windows 11 and Ubuntu?

---

### Post by chrisg-32 on 2022-11-04
Lol, I do not because most of the stuff I care about is on my desktop or online. I was trying to avoid reinstalling all the stuff I have downloaded on Ubuntu. When I formatted it notably the thing said it would not delete any data so I don't know if that means there is hope

---

### Post by chrisg-32 on 2022-11-04
> **oldfred said:**
> While p6 says Linux, the report showed none of the files it normally shows from a Linux install.
It might first try fsck on nvme0n1p6.

```
To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required, Run both commands as they have different parameters.
sudo e2fsck -C0 -p -f -v /dev/nvme0n1p6
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/nvme0n1p6


```

Post back if any errors.

Then I would see if Boot-Repair  correctly sees your install.
And/or use advanced mode to totally reinstall grub and latest kernel.
Still unable to recognize the linux install, I think I may be stuck reinstalling. I don't know if this was clear but the only reason that I could access nvme0n1p6 was because I formatted it as ext4, what both windows and the live usb ubuntu saw as unallocated space.

---

