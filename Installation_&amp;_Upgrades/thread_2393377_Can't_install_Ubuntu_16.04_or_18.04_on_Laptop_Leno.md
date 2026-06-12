---
title: "Can't install Ubuntu 16.04 or 18.04 on Laptop Lenovo Legion Y520"
date: 2018-06-02
forum: Installation &amp; Upgrades
---

### Post by 2pacho on 2018-06-02
I have this issue with Ubuntu (and I think that I tried Lubuntu too) :
What happens is that the pc freezes after installing or it wont start up at all... Sometimes the liveUsb works sometimes it doesn't.
The strange thing is that I can install Linux Mint 18.3 and use it...

This picture shows my error

[IMG]https://i.imgur.com/BdPHhyl.jpg[/IMG]

This is my Laptop's short info
```

H/W path       Device     Class          Description
====================================================
                          system         80WK (LENOVO_MT_80WK_BU_idea_FM_Lenovo Y520-15IKBN)
/0                        bus            Provence-5R1
/0/0                      memory         128KiB BIOS
/0/4                      processor      Intel(R) Core(TM) i7-7700HQ CPU @ 2.80GHz
/0/4/5                    memory         256KiB L1 cache
/0/4/6                    memory         1MiB L2 cache
/0/4/7                    memory         6MiB L3 cache
/0/24                     memory         8GiB System Memory
/0/24/0                   memory         8GiB SODIMM Synchronous 2400 MHz (0,4 ns)
/0/24/1                   memory         [empty]
/0/24/2                   memory         [empty]
/0/24/3                   memory         [empty]
/0/100                    bridge         Intel Corporation
/0/100/1                  bridge         Sky Lake PCIe Controller (x16)
/0/100/1/0                display        NVIDIA Corporation
/0/100/2                  display        Intel Corporation
/0/100/14                 bus            Sunrise Point-H USB 3.0 xHCI Controller
/0/100/14/0    usb1       bus            xHCI Host Controller
/0/100/14/0/6             multimedia     EasyCamera
/0/100/14/0/b             communication  Bluetooth wireless interface
/0/100/14/1    usb2       bus            xHCI Host Controller
/0/100/14.2               generic        Sunrise Point-H Thermal subsystem
/0/100/16                 communication  Sunrise Point-H CSME HECI #1
/0/100/17                 storage        Sunrise Point-H SATA Controller [AHCI mode]
/0/100/1c                 bridge         Sunrise Point-H PCI Express Root Port #2
/0/100/1c/0               generic        O2 Micro, Inc.
/0/100/1c.2               bridge         Sunrise Point-H PCI Express Root Port #3
/0/100/1c.2/0  wlp3s0     network        Intel Corporation
/0/100/1c.3               bridge         Sunrise Point-H PCI Express Root Port #4
/0/100/1c.3/0  enp4s0     network        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
/0/100/1f                 bridge         Sunrise Point-H LPC Controller
/0/100/1f.2               memory         Memory controller
/0/100/1f.3               multimedia     Intel Corporation
/0/100/1f.4               bus            Sunrise Point-H SMBus
/0/1           scsi2      storage        
/0/1/0.0.0     /dev/sda   disk           1TB ST1000LM035-1RK1
/0/1/0.0.0/1              volume         511MiB Windows FAT volume
/0/1/0.0.0/2   /dev/sda2  volume         923GiB EXT4 volume
/0/1/0.0.0/3   /dev/sda3  volume         8065MiB Linux swap volume
/1                        power          CRB Battery 0
/2                        power          OEM Define 5


```

Any recommendations'?

---

### Post by oldfred on 2018-06-02
Your nVidia will need nomodeset for installer & first boot or until you install the proprietary nVidia driver from Ubuntu repository. Do not install directly from nVidia.

Are you only installing Ubuntu in UEFI boot mode?
How you boot install media is then how it installs.
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[URL="http://ubuntuforums.org/showthread.php?t=1613132"]http://ubuntuforums.org/showthread.php?t=1613132
[/URL]
 Lenovo Legion Y520-15I  Installer does not detect SSD and HDD: Ubuntu 16.04 LTS
[https://ubuntuforums.org/showthread.php?t=2359208](https://ubuntuforums.org/showthread.php?t=2359208) [URL="http://ubuntuforums.org/showthread.php?t=1613132"]

[/URL]Have you updated UEFI? Required for all PCs.

Is/Are drives in RAID mode. If RAID 0, breaking RAID can cause major issues. Be sure to have good backups. 
Drives need to be in AHCI mode, not RAID, IDE, nor some Intel SRT thing. But if still using Windows make sure you have added the AHCI driver first.

---

