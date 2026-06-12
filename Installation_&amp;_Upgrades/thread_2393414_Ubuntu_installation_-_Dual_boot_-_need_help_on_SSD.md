---
title: "Ubuntu installation - Dual boot - need help on SSD HDD partition"
date: 2018-06-03
forum: Installation &amp; Upgrades
---

### Post by surestce on 2018-06-03
I have pre-installed Windows 10 system. I want to install Ubuntu as dual boot. My system has 250 GB SSD in which Windows 10 is installed. I have partitioned it 2. 1 part has 150 GB with Win installed. Other 1 has 100 GB Unallocated.

The system has 1 TB HDD also, partitioned into 2 to use 1 part (900 GB) for Windows & 100 GB for Linux? I read somewhere that Linux can read / write files from NFTS but reverse is not possible, so only 900 vs 100 GB. 

Questions:
1. Can I install Ubuntu in this 100 GB partitioned SSD? Is this much space required? Planning to allocate 32GB for swap memory (16 GB RAM can be extended to 32 GB), is this memory fine? 

2. What will happen to rest of the space in 100 GB SSD that allocated for Linux? Can I use remaining space for storing other files from Windows/ Linux after installation? 

3. How can I make a root that point to 2nd partition of HDD as storage system? 

Please help.

Thanks in advance.

---

### Post by Dennis N on 2018-06-03
I usually will allocate a 25 gB partition for Ubuntu installs, so no - you don't need 100 gB to install it. Ubuntu no longer needs a swap partition - it automatically creates a swap file when no swap partition is present during installation. If you have a swap partition, it will be used instead of the swap file. The computer I am using has 4 gB swap partition, but 12 gB RAM. On this desktop system, I've never seen the swap partition being used.

Remaining unallocated space can be used for a data partition. I have one. I don't have a Windows OS present, so my data partition is ext4 format. I mount it at startup with a line in /etc/fstab file.

---

### Post by oldfred on 2018-06-03
If a newer user using a  /home partition is the easier way to separate system from data. It then automatically gives you ownership and permissions and adds it to fstab for mounting. But you have to understand a bit about partitioning or are willing to learn.

To have more than just the default / (root) partition you need to use the Something Else install option. You can create partitions during install or in advance with gparted, but still have to choose (change button) which partition is / and which is /home.

If using NTFS for data, best to mount that in fstab, but you will have to do that after your install. And temporarily you can auto mount just by selecting it with Nautilus.  

Since pre-installed Windows, it will be a UEFI system with UEFI install of Windows. You need to install Ubuntu in UEFI boot mode. How you boot install media UEFI or BIOS is then how it installs.
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [URL="https://help.ubuntu.com/community/UEFI"]https://help.ubuntu.com/community/UEFI
      [/URL]
 Also shows Windows 10 screens or similar to Windows 8
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi) 
    
 MBR(for BIOS) or gpt(for UEFI) partitions:
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)[URL="https://help.ubuntu.com/community/UEFI"]
[/URL]

---

### Post by surestce on 2018-06-03
Please note that Windows 10 is UEFI  enabled and Secure Boot enabled.

---

### Post by oldfred on 2018-06-03
Ubuntu will install and work with UEFI Secure Boot on.
But not if you need proprietary drivers for video or Internet as Ubuntu cannot verify if proprietary driver is secure or not, so cannot enable trust chain.

---

