---
title: "File System Errors - Ubuntu 24.04 Install on new hardware."
date: 2024-06-19
forum: Installation &amp; Upgrades
---

### Post by patrick_g2 on 2024-06-19
I have build a new computer and installed Ubuntu 24.04. The hardware and system specs are as follows:

System:   Kernel: 5.15.0-91-generic x86_64 bits: 64 compiler: gcc v: 11.4.0 Desktop: Cinnamon 6.0.4
    tk: GTK 3.24.33 wm: muffin vt: 7 dm: LightDM 1.30.0 Distro: Linux Mint 21.3 Virginia
    base: Ubuntu 22.04 jammy
Machine: Type: Desktop Mobo: Gigabyte model: X670 AORUS ELITE AX v: 1.3 serial
    UEFI: American Megatrends LLC. v: FB date: 11/08/2023
CPU: Info: 12-core model: AMD Ryzen 9 7900X bits: 64 type: MT MCP smt: enabled arch: Zen 3 rev: 2
Graphics: Device-1: RX 580 8GB Graphics Card, 2048SP,GDDR5,256 Bit Graphics Card for Gaming PC,PCIE 3.0
Drives:
  Local Storage: total: 1.4 TiB used: 10.77 GiB (0.7%)
  ID-1: /dev/nvme0n1 vendor: Gigabyte model: GP-AG41TB size: 931.51 GiB speed: 63.2 Gb/s
    lanes: 4 type: SSD serial: <filter> rev: EGFM13.0 temp: 34.9 C scheme: GPT
  ID-2: /dev/nvme1n1 vendor: Silicon Power model: SPCC M.2 PCIe SSD size: 476.94 GiB
    speed: 31.6 Gb/s lanes: 4 type: SSD serial: <filter> rev: ECFM22.6 temp: 34.9 C scheme: GPT
  ID-3: /dev/sda type: USB model: Mass Storage Device size: 6TB type: N/A serial: <filter>
    rev: 1.00 scheme: MBR

I have successfully loaded 24.04 (several times) and have begun loading the data from the old machine. I use a 500gb USB system to transport the data from old to new machines. I cut and paste data from the USB to the SSD or HDD that will be it's new home then go away and let the file transfers happen (several times). Each time at some time during the file transfer processes the machine locks up. The lockup is so complete that the mouse and keyboard do not function. I have to physically shut the power off to the machine. When I power back up, I run the Disks utility to check the file systems of the active drives - they always need to be repaired. Once repaired, data access on the active drives is dodgy at best. A few times, accessing data locks the system up again. 

Note: there are no applications running on the new machine other than the Disks utility to check/repair file systems. before each reload, I reformat the partitions on the data drives so I have a virgin install.

---

### Post by patrick_g2 on 2024-06-19
Sorry, that system image was from an attempted Mint install that failed. The correct distro is: Ubuntu 22.04.4 LTS

---

### Post by grahammechanical on 2024-06-19
What size is the Ubuntu partition? I experience something strange on an install of Ubuntu 24.04. It is on a 74 GB partition and sometimes when I am upgrading a certain library app that requires a 3GB download of doing a zsync of the 24.10 ISO image the system will suspend due to lack of keyboard activity and it will not resume. The power light is still on but only a power off and then on gets back to a working system. Sometimes I get a warning that root is running out of space.

I think that this is happening because Ubuntu now uses a swap file that varies in size instead of a fixed sized swap partition. I am considering enlarging the Ubuntu 24.04 partition.

P.S. I think that 22.04 uses a swap file as well. I may be wrong about that.

Regards

---

### Post by patrick_g2 on 2024-06-19
Ubuntu is installed on the 500GB drive and it sets the partition size at install.

---

### Post by oldfred on 2024-06-19
This cannot be right or you did not correctly partition it.
> ID-3: /dev/sda type: USB model: Mass Storage Device size: [COLOR=#ff0000]6TB[/COLOR] type: N/A serial: <filter>
    rev: 1.00 scheme: [COLOR=#ff0000]MBR[/COLOR]

MBR was designed in the 1980s (or before?) and has a hard limit of 2TB as back then MB was large.
You have to use gpt partitioning for any drive over 2TB.

What does this say about drive?
sudo gdisk -l /dev/sda

[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

man fdisk # disk labels section:
"GPT is always a better choice than MBR, especially on modern hardware with a UEFI boot loader."

---

### Post by patrick_g2 on 2024-06-19
Thanks for that. That hardware image was taken before I started partitioning the new 6TB drive. The following is current config:

GPT fdisk (gdisk) version 1.0.8

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 11721045168 sectors, 5.5 TiB
Model: WDC WD6004FZWX-0
Sector size (logical/physical): 512/4096 bytes
Disk identifier (GUID): 2238AD06-0A9B-49FF-9634-0AC2C66AA385
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 11721045134
Partitions will be aligned on 2048-sector boundaries
Total free space is 3908547693 sectors (1.8 TiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048      7812499455   3.6 TiB     8300  4TB

The machine's Bios automatically handles all disks as UEFI.

 a side question: This is 2024 why does the Ubuntu's Disk utility NOT handle drives larger than 2TB.

---

### Post by oldfred on 2024-06-19
I have never used Disk Utility for anything other than changes partition labels.
It had done strange things for me in the past.
I prefer gparted.

---

### Post by TheFu on 2024-06-20
+1 for gparted or anything except Gnome Disk Manager. I've been burned too many times.

---

