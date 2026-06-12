---
title: "Booting from ZFS"
date: 2022-04-26
forum: Installation &amp; Upgrades
---

### Post by xparhelion on 2022-04-26
When doing my own research on how to mount ZFS to root and boot from it, I had attempted to mount and boot from the device, to no avail. Creating mounts in the zfs_member partition results in the following error:
```
mount: /mnt/boot/grub: unknown filesystem type 'zfs_member'.
```
I have already successfully created the external partitions [nvme0n1p1-nvme0n1p3 and sda1-sda2] with the ZFS pools necessary to run this operation. My question is how do I boot from an encrypted RAID0 config on ZFS using rEFInd?

```

// System Drives - 
sda           8:0    0 223.6G  0 disk 
&#9500;&#9472;sda1        8:1    0 111.8G  0 part 
&#9492;&#9472;sda2        8:2    0 111.8G  0 part 
sdb           8:16   1  28.9G  0 disk 
&#9500;&#9472;sdb1        8:17   1   3.4G  0 part /cdrom
&#9500;&#9472;sdb2        8:18   1   4.1M  0 part /boot/efi
&#9500;&#9472;sdb3        8:19   1   300K  0 part 
&#9492;&#9472;sdb4        8:20   1  25.5G  0 part /var/crash
                                      /var/log
nvme0n1     259:0    0 476.9G  0 disk 
&#9500;&#9472;nvme0n1p1 259:1    0   512M  0 part 
&#9500;&#9472;nvme0n1p2 259:4    0    16G  0 part 
&#9492;&#9472;nvme0n1p3 259:5    0 460.4G  0 part

// System Info - 
/0                                      bus         GA15DH
/0/23/0                                 memory      8GiB DIMM DDR4 Synchronous Unbuffered (Unregistered)
/0/23/1                                 memory      8GiB DIMM DDR4 Synchronous Unbuffered (Unregistered)
/0/29                                   processor   AMD Ryzen 7 3700X 8-Core Processor
/0/100                                  bridge      Starship/Matisse Root Complex
/0/100/0.2                              generic     Starship/Matisse IOMMU
/0/100/1.1                              bridge      Starship/Matisse GPP Bridge
/0/100/1.1/0            /dev/nvme0      storage     INTEL SSDPEKNW512G8
/0/100/1.3                              bridge      Starship/Matisse GPP Bridge
/0/100/1.3/0                            bus         400 Series Chipset USB 3.1 XHCI Controller
/0/100/1.3/0.1          scsi5           storage     400 Series Chipset SATA Controller
/0/100/1.3/0.1/0.0.0    /dev/sda        disk        240GB SATA SSD
/0/100/1.3/0.1/0.0.0/1  /dev/sda1       volume      111GiB Linux filesystem partition
/0/100/1.3/0.1/0.0.0/2  /dev/sda2       volume      111GiB HPFS/NTFS partition
/0/100/1.3/0.2                          bridge      400 Series Chipset PCIe Bridge
/0/100/1.3/0.2/6/0      wlp7s0          network     RTL8822CE 802.11ac PCIe Wireless Network Adapter
/0/100/1.3/0.2/7                        bridge      400 Series Chipset PCIe Port
/0/100/1.3/0.2/7/0      enp8s0          network     RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
/0/100/3.1                              bridge      Starship/Matisse GPP Bridge
/0/100/3.1/0                            display     TU116 [GeForce GTX 1660 Ti]
/0/100/3.1/0.2                          bus         TU116 USB 3.1 Host Controller
/0/100/3.1/0.3                          bus         TU116 USB Type-C UCSI Controller
/0/1/0.0.0              /dev/sdb        disk        31GB USB DISK 3.0
/0/1/0.0.0/0            /dev/sdb        disk        31GB 
/0/1/0.0.0/0/1          /dev/sdb1       volume      3481MiB data partition
/0/1/0.0.0/0/2          /dev/sdb2       volume      15EiB Windows FAT volume
/0/1/0.0.0/0/3          /dev/sdb3       volume      299KiB data partition
/0/1/0.0.0/0/4          /dev/sdb4       volume      25GiB EXT4 volume

```

---

### Post by CharlesA on 2022-04-26
Why do you want to use rEFind instead of grub?

I've successfully set up a ZFS root using both LUKS and ZFS Encryption with the instructions here:
[https://openzfs.github.io/openzfs-docs/Getting%20Started/Ubuntu/Ubuntu%2020.04%20Root%20on%20ZFS.html](https://openzfs.github.io/openzfs-docs/Getting%20Started/Ubuntu/Ubuntu%2020.04%20Root%20on%20ZFS.html)

---

