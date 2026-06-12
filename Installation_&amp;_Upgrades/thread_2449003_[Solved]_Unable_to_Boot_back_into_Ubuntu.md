---
title: "[Solved] Unable to Boot back into Ubuntu"
date: 2020-08-18
forum: Installation &amp; Upgrades
---

### Post by angelofraietta2 on 2020-08-18
Greetings
I have a THINKPAD T490 and it looks like the Lenovo will not let me fix grub. I suspect that the machine lost power and coupled with a Lenovo update, it will not let me get back into Ubuntu

I have tried boot-repair and this is what it has put in pastebin

[http://paste.ubuntu.com/p/tpWkGGHHTy/](http://paste.ubuntu.com/p/tpWkGGHHTy/)

Any help to get me booted back into Ubuntu would be great.

Thanks again

---

### Post by oldfred on 2020-08-18
Boot-Repair is not seeing the ESP.
The ESP folder has both Windows & Ubuntu boot files. So it was seen before.
Often issue is Windows turns fast start up back on locking partitions. 
Check Windows fast start up is still off.
A few systems have a UEFI setting to prevent write (not sure how). Check settings.
And sometimes ESP gets corrupted and needs dosfsck or chkdsk from Windows.

dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted
sudo dosfsck -t -a -w /dev/nvme0n1p1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

You do not have an UEFI boot entry for Ubuntu in UEFI. Boot-Repair shows results from this command:
sudo efibootmgr -v

Full reinstall of grub will update UEFI using efibootmgr.
You can try adding an entry.
Typical example, but yours is an NVMe drive.
sudo efibootmgr -c  -l \EFI\ubuntu\shimx64.efi -L "Ubuntu" -d /dev/sdX -p Y
sdX is drive, Y is efi partition default is sda and first partition, so only required if not sda1
So more like this (for others that may not have p1 as ESP):
sudo efibootmgr -c -L "Ubuntu" -l "\EFI\ubuntu\shimx64.efi" -d /dev/nvme0nX -p Y
Or specifically using first partition on first NVMe drive:
sudo efibootmgr -c -L "ubuntu" -l "\EFI\ubuntu\shimx64.efi" -d /dev/nvme0n1 -p 1

---

### Post by angelofraietta2 on 2020-08-18
Greetings.

First, thanks for taking the time to have a look. It is not resolved. Please find my comments

> **oldfred said:**
> Boot-Repair is not seeing the ESP.
The ESP folder has both Windows & Ubuntu boot files. So it was seen before.
Often issue is Windows turns fast start up back on locking partitions. 
Check Windows fast start up is still off.


It is off.

> **oldfred said:**
> 
dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted
sudo dosfsck -t -a -w /dev/nvme0n1p1
The -a seems to help in clearing dirty bit


It is unmounted already. I get this
[B]fsck.fat 4.1 (2017-01-24)
/dev/nvme0n1p1: 212 files, 15596/65536 clusters[/B]
This did not show any errors


I am lost from here. I don't know what you are actually asking me to do
> **oldfred said:**
> 

You do not have an UEFI boot entry for Ubuntu in UEFI. Boot-Repair shows results from this command:
sudo efibootmgr -v

Full reinstall of grub will update UEFI using efibootmgr.
You can try adding an entry.
Typical example, but yours is an NVMe drive.
sudo efibootmgr -c  -l \EFI\ubuntu\shimx64.efi -L "Ubuntu" -d /dev/sdX -p Y
sdX is drive, Y is efi partition default is sda and first partition, so only required if not sda1
So more like this (for others that may not have p1 as ESP):
sudo efibootmgr -c -L "Ubuntu" -l "\EFI\ubuntu\shimx64.efi" -d /dev/nvme0nX -p Y
Or specifically using first partition on first NVMe drive:
sudo efibootmgr -c -L "ubuntu" -l "\EFI\ubuntu\shimx64.efi" -d /dev/nvme0n1 -p 1

---

### Post by oldfred on 2020-08-18
See if this adds a working entry, since you still have the Ubuntu .efi boot files in the ESP.

Or specifically using first partition on first NVMe drive:
sudo efibootmgr -c -L "ubuntu" -l "\EFI\ubuntu\shimx64.efi" -d /dev/nvme0n1 -p 1

---

### Post by angelofraietta2 on 2020-08-19
That was the winner. Thanks a lot. Much appreciated. I will mark this thread as solved.

---

