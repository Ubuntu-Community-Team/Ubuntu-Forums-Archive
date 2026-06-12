---
title: "Installing with OS X and Win 7"
date: 2010-02-23
forum: Installation &amp; Upgrades
---

### Post by OliverBarker on 2010-02-23
Well I'm an apple person. So naturally when I heard about hackintoshing I took it. Buying several HP minis and installing OS X on them. Thank god for iDeneb 1.3! Anyway, to the topic. I wanted to triple boot OS X, Windows 7 and Ubuntu 9.04. The HP Mini 110 will be my play toy.

Now, I partitioned it as followed and have successfully installed OS X and Windows 7. ANd have a partition for Ubuntu.

*Mac OS Extended Journaled - Mac OS X 10.5.5 (soon updating) - 20Gb
*NFTS - Windows 7 Ultimate - 16Gb
*FAT32 - FOR UBUNTU - 10Gb
*FAT32 - Data Partition - 100Gb aprox.

Using the 9.04 live disk how can I install Ubuntu on the sda3 partition without erasing the others, yet still being able to select it using Chameleon Bootloader at startup?

---

### Post by recluce on 2010-02-23
> **OliverBarker said:**
> Well I'm an apple person. So naturally when I heard about hackintoshing I took it. Buying several HP minis and installing OS X on them. Thank god for iDeneb 1.3! Anyway, to the topic. I wanted to triple boot OS X, Windows 7 and Ubuntu 9.04. The HP Mini 110 will be my play toy.

Now, I partitioned it as followed and have successfully installed OS X and Windows 7. ANd have a partition for Ubuntu.

*Mac OS Extended Journaled - Mac OS X 10.5.5 (soon updating) - 20Gb
*NFTS - Windows 7 Ultimate - 16Gb
*FAT32 - FOR UBUNTU - 10Gb
*FAT32 - Data Partition - 100Gb aprox.

Using the 9.04 live disk how can I install Ubuntu on the sda3 partition without erasing the others, yet still being able to select it using Chameleon Bootloader at startup?

FAT32 is the wrong format for Ubuntu, but the installer will let you format to something more suitable (like EXT3). FAT32 in the data partition will mean a file size limit of 2 GB. If you have a way to access NTFS from MAC OS, reformatting the data partition to NTFS would be the better choice.

As to the Ubuntu install: the "Alternate install CD" should have an option to install GRUB to the Ubuntu partition and not the MBR (master boot record). This means that any bootloader that allows chainloading will be able to call up GRUB to load Ubuntu. So if Chameleon can chainload something, this should work.

More on "Legacy" Grub on this excellent page:

[http://members.iinet.net.au/~herman546/p15.html](http://members.iinet.net.au/~herman546/p15.html)

---

