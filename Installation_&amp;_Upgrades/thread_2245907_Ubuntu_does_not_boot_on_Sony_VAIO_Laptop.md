---
title: "Ubuntu does not boot on Sony VAIO Laptop"
date: 2014-09-27
forum: Installation &amp; Upgrades
---

### Post by lachlan-s-peter on 2014-09-27
I have a Sony Laptop running Windows 8.1 but want to install Ubuntu. I created a live disk and did the installation. The BIOS has UEFI enabled but the secure boot is not.
When I did the partitioning  the result was 
free space 1MB - automatically created
sda1 efi 256MB
sda2 ext4 240GB
sda3 swap 8096MB

After installation, the system did not boot. I ran boot-repair as indicated on [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) but still no luck.
I modified the partitions as outlined in [http://www.linuxbsdos.com/2014/02/05/gpt-disk-partitioning-guide-for-ubuntu-13-10-on-a-pc-with-uefi-firmware/](http://www.linuxbsdos.com/2014/02/05/gpt-disk-partitioning-guide-for-ubuntu-13-10-on-a-pc-with-uefi-firmware/) with the result
free space 1MB
reserve BIOS 1MB
efi 256MB
EXT4 240GB
swap 8096MB

When running the boot-repair note the URL is 8437692. When I then try to run boot-repair again it gives me the message 'BIOS-Boot detected. You may want to retry after deactivating the [separate /boot/efi partition option]'

When I boot the system, I get the Sony VAIO BIOS saying there is no operating system.

I have redone this with various different options, and boot-repair each time. I have tried disabling the UEFI and running in Legacy mode by the system just comes up with 'No opertaing system'.

Any ideas on how to proceed would be appreciated?

---

