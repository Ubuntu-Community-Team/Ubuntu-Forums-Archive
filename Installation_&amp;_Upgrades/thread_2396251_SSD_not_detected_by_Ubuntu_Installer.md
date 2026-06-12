---
title: "SSD not detected by Ubuntu Installer"
date: 2018-07-12
forum: Installation &amp; Upgrades
---

### Post by akashpanda123 on 2018-07-12
I have recently bought a new HP laptop with pre-installed Windows 10. 
ModelNo. HP Pavilion x360 cd0056tx

I created an UEFI enabled USB bootable of Ubuntu 18.04. 

I booted using my USB drive. Then in the installation process, I am not able to see my SSD, where I would like to install Ubuntu.
Please help me in the regards.

---

### Post by oldfred on 2018-07-12
Is Windows fast start up on? That is hibernation and the Linux NTFS driver will not mount hibernated file systems, so then installer cannot see it.
Is system set for AHCI, not RAID nor IDE. If RAID, install AHCI drivers into Windows before changing or else you have to constantly switch setting, until you do install drivers.

Post this from live installer in live mode:
sudo parted -l
sudo gdisk -l /dev/sda
If drive is not sda, use whatever it is, maybe nvme0n1 or other device?

---

