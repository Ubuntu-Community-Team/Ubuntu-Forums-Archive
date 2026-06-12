---
title: "Dual boot, m2 HDs with shared m2 drive"
date: 2018-11-15
forum: Installation &amp; Upgrades
---

### Post by krcull on 2018-11-15
Have new Dell 5230 with 3 m2 drives. Attempting to install windows 10 pro on one, ubuntu 18.04 on the 2nd and have the 3rd as a shared drive between them. 

I can get the two m2 drives to fire up both OSs but as soon as I add the 3rd drive it break the boot loader. I’ve been trying multiple sequences of installations and formatting and always never quite get there. Closest is having both m2 drives with their respective OS being loaded by grub2. But as soon as I add the third drive all hell breaks loose.

It’s been 3 days of intermittent hell. Dell support of course was useless.

Ideas? Instructions? Links??

---

### Post by mitesh.agrwl on 2018-11-15
Please paste the output of following commands here:

**$ inxi -Fz **(If it is not installed, install using **$ sudo apt-get install inxi**)
[B]$ sudo lshw -class storage
$ sudo lshw -class disks[/B]

---

### Post by krcull on 2018-11-15
Thank you for the reply. Of course I've ended up solving this just after posting. Now have a stable machine with windows 10 on 1 m2 drive, ubuntu 18.04 on a 2nd m2 drive and a 3rd shared m2 drive

I've included the requested info below for completeness. 

Steps I took to get my system to work: 
- Removed all drives from machine except 1st m2 drive to install Windows
- Installed windows-10 on 1st m2 drive (ID 3 from inxi)
- Installed 2nd m2 drive (shared storage, ID 2 from inxi) and formatted ntfs from within windows
- Installed 3rd m2 drive (ID 1 from inxi) I had been installing ubuntu on and deleted all partitions so it was empty
- installed ubuntu from USB stick with the option "alongside windows boot manager" (i.e. I let the ubuntu installation manage the partitions, etc)

Now grub2 is allowing me to choose either ubuntu or windows at boot and I can access the 3rd shared drive from both OS's which is what I wanted. 


$ inxi -Fz
System:    Host: XXXX Kernel: 4.15.0-39-generic x86_64 bits: 64
           Desktop: Gnome 3.28.3 Distro: Ubuntu 18.04.1 LTS
Machine:   Device: laptop System: Dell product: Precision 7530 serial: N/A
           Mobo: Dell model: 07NCNV v: A00 serial: N/A
           UEFI: Dell v: 1.4.2 date: 09/10/2018
Battery    BAT0: charge: 41.8 Wh 43.0% condition: 97.0/97.0 Wh (100%)
CPU:       6 core Intel Xeon E-2176M (-MT-MCP-) cache: 12288 KB
           clock speeds: max: 4400 MHz 1: 1219 MHz 2: 2700 MHz 3: 2752 MHz
           4: 2693 MHz 5: 3056 MHz 6: 2613 MHz 7: 2604 MHz 8: 2613 MHz
           9: 2722 MHz 10: 2601 MHz 11: 2203 MHz 12: 2658 MHz
Graphics:  Card-1: Intel Device 3e94
           Card-2: NVIDIA Device 1cba
           Display Server: x11 (X.Org 1.19.6 ) drivers: i915,nouveau
           Resolution: 3840x2160@60.00hz
           OpenGL: renderer: Mesa DRI Intel HD Graphics (Coffeelake 3x8 GT2)
           version: 4.5 Mesa 18.0.5
Audio:     Card-1 Intel Device a348 driver: snd_hda_intel
           Card-2 NVIDIA GP107GL High Def. Audio Controller
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.15.0-39-generic
Network:   Card-1: Intel Ethernet Connection (7) I219-LM driver: e1000e
           IF: eno1 state: down mac: <filter>
           Card-2: Intel Device 2526 driver: iwlwifi
           IF: wlp112s0 state: up speed: N/A duplex: N/A mac: <filter>
Drives:    HDD Total Size: 512.1GB (1.5% used)
           ID-1: /dev/nvme0n1 model: Samsung_SSD_970_PRO_512GB size: 512.1GB
           ID-2: /dev/nvme1n1 model: Samsung_SSD_970_EVO_2TB size: 2000.4GB
           ID-3: /dev/nvme2n1 model: PM981_NVMe_Samsung_256GB size: 256.1GB
Partition: ID-1: / size: 468G used: 7.3G (2%) fs: ext4 dev: /dev/nvme0n1p5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 40.0C mobo: N/A gpu: 51.0
           Fan Speeds (in rpm): cpu: 0 fan-2: 0
Info:      Processes: 327 Uptime: 12 min Memory: 2172.9/31930.5MB
           Client: Shell (bash) inxi: 2.3.56 



$ sudo lshw -class storage
  *-storage                 
       description: SATA controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 17
       bus info: pci@0000:00:17.0
       version: 10
       width: 32 bits
       clock: 66MHz
       capabilities: storage msi pm ahci_1.0 bus_master cap_list
       configuration: driver=ahci latency=0
       resources: irq:133 memory:b5634000-b5635fff memory:b5637000-b56370ff ioport:4090(size=8) ioport:4080(size=4) ioport:4060(size=32) memory:b5636000-b56367ff
  *-storage
       description: Non-Volatile memory controller
       product: Samsung Electronics Co Ltd
       vendor: Samsung Electronics Co Ltd
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: storage pm msi pciexpress msix nvm_express bus_master cap_list
       configuration: driver=nvme latency=0
       resources: irq:16 memory:b5500000-b5503fff
  *-storage
       description: Non-Volatile memory controller
       product: Samsung Electronics Co Ltd
       vendor: Samsung Electronics Co Ltd
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: storage pm msi pciexpress msix nvm_express bus_master cap_list
       configuration: driver=nvme latency=0
       resources: irq:16 memory:b5400000-b5403fff
  *-storage
       description: Non-Volatile memory controller
       product: Samsung Electronics Co Ltd
       vendor: Samsung Electronics Co Ltd
       physical id: 0
       bus info: pci@0000:71:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: storage pm msi pciexpress msix nvm_express bus_master cap_list
       configuration: driver=nvme latency=0
       resources: irq:16 memory:b5100000-b5103fff

---

### Post by oldfred on 2018-11-15
Often disconnecting a drive, cause UEFI to lose UEFI boot entry. Most systems seem to find Windows again from ESP, but not any other systems. 
You then may need to use efibootmgr to add entry or re-install grub which uses efibootmgr to add entry to UEFI menu.

Many with SSD have had to update firmware and Dell's UEFI for system to work with Ubuntu.

Windows updates may turn Windows fast start up which is hibernation back on and that sets hibernation flag on all NTFS partitions. If the Linux NTFS driver sees a hibernation flag it will not mount partition read/write. If issues writing to NTFS shared data double check that Windows did not turn on fast start up.

---

