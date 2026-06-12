---
title: "How to remove &quot;ubuntu&quot; entry from the UEFI boot options?"
date: 2023-01-09
forum: Installation &amp; Upgrades
---

### Post by bsh on 2023-01-09
Hey all,
I've been using a PC to install Xubuntu 22.04 from a USB stick to an USB HDD. The PC has Windows 10 on it, on an SSD, and there's also a HDD.
Even though I have manually set up the partitions and explicitly selected grub to be placed on the USB HDD, it somehow did create an entry on the windows drive efi partition and set as default, so once I've removed the USB HDD it rebooted into the grub rescue promtp.
I have deleted this ubuntu entry off the windows disk's efi partition, and it boots normal now, but when I go to the F12 boot menu on Post, it still lists an "ubuntu" entry.
I guess this is somewehre in the NVRAM or something? Or where else could this come from?
Is there a way to edit and remove this? Through the efi shell maybe? All I found is bcdedit but that is for the stuff on the windows efi partition, or third party tools...

---

### Post by oldfred on 2023-01-09
You can use efibootmgr.
man efibootmgr

sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B


Ubuntu's Ubiquity installer only installs grub to first drive's ESP.
Since also bitten by old bug, please add that it applies to you.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
They will never fix it, as now they are developing a new installer to replace ubiquity.

Bug report also has many work arounds for installing to any second drive or an external drive.

External drives all boot from /efi/Boot/bootx64.efi which is a drive entry like the live installer.

---

### Post by bsh on 2023-01-10
thanks. I'll try that. seems dangerous though... I have approximately 0 knowledge about efi. :)
in the mean time I tried bcdedit on windows, and it still displays "ubuntu", even though i have deleted that whole folder from the efi partition. iremoved the entry with bcdedit but it is still available on POST, and after a reboot bcdedit shows it again. I assume, there's a list or config file on the efi partition that still contains this entry even if the files are deleted. i guess bootrec /rebuildbcd would work...?

---

### Post by oldfred on 2023-01-10
Your UEFI/BIOS has its own NVRam which stores a boot entry. This just shows the entries. Many may be system defaults.
sudo efibootmgr -v

---

