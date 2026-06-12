---
title: "No dual-boot, install Ubuntu as only OS"
date: 2019-10-08
forum: Installation &amp; Upgrades
---

### Post by donsy on 2019-10-08
I'm getting ready to buy a new Dell laptop and want to set it up with Ubuntu as the only OS -- no dual-boot. I don't want to use the "erase disk" option because I want to create separate / and /home partitions. So my question is: if I use Gparted to delete every partition except /dev/sda1 (the EFI partition), create the partitions (and a swap), and then choose the "something else option" will that work? Should keep the EFI partition as is or should I format it?

---

### Post by oldfred on 2019-10-08
You also do not need swap as now Ubuntu uses a swap file.

You will need an ESP - efi system partition. 

I would fully backup system. 
We get many users who only want Ubuntu. But then find one application or game that must have Windows. Or later want to sell system and need to have Windows to sell it. 
One user posted he regularly gets a new system, and immediately removes Windows HDD and installs a new SSD for Ubuntu. Then when selling it puts HDD back in and does not have to worry about any of his data on it.

Dell typically has a few extra requirements over a vanilla install.
You need to update UEFI, even if new system, it may not be newest version.
You need to update SSD firmware.
You need to change drives to AHCI from Intel RST or RAID setting in UEFI.

Steps to install in UEFI boot mode in link in my signature.

Dell with NVMe needs AHCI & boot option nvme_load=YES
[https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en](https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en)
[https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571](https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571)
[https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en](https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en)

---

### Post by donsy on 2019-10-08
Thanks. If I keep the Windows EFI partition as it came from Windows will Ubuntu use it as it is or should I delete it and create a new one?

---

### Post by oldfred on 2019-10-08
Windows typically uses 100MB. And that is large enough for both Windows .efi boot files & Ubuntu's .efi boot files and configuration files that are in ESP.
But for future use, I suggest 500MB for the ESP. I only use the smaller ESP on smaller flash drives.

---

### Post by donsy on 2019-10-08
Thanks for your help.

---

