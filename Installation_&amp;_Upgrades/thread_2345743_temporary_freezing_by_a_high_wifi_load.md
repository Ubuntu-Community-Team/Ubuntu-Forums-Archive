---
title: "temporary freezing by a high wifi load"
date: 2016-12-07
forum: Installation &amp; Upgrades
---

### Post by ah32 on 2016-12-07
Hello,

my notebook is continuously freezing by a high wifi load on any linux distro.
I tested:
- ubuntu 16.04, 16.10, 17.04 and the current mainline kernel
- manjaro
- fedora

- ram check with memtest
- to fix the wifi antenna:
        echo "options rtl8723be swenc=1 fwlps=0 ips=0 ant_sel=1" | sudo tee /etc/modprobe.d/rtl8723be.conf
- changed /proc/irq/42/smp_affinity to f


I initially asked at [ubuntuusers.de]("https://forum.ubuntuusers.de/topic/friert-ein-bei-hoher-wlan-nutzung/")

I hope maybe someone here has another hint?


[http://pastebin.com/76xJC0qz](http://pastebin.com/76xJC0qz)

Thanks!

```
H/W path                   Device      Class          Description
=================================================================
                                       system         HP Notebook (X7F58EA#ABD)
/0                                     bus            81F5
/0/0                                   memory         128KiB BIOS
/0/f                                   memory         4GiB System Memory
/0/f/0                                 memory         SODIMM [empty]
/0/f/1                                 memory         4GiB SODIMM DDR3 Synchronous Unbuffered (Unregistered) 1600 MHz (0.6 ns)
/0/17                                  processor      AMD E2-7110 APU with AMD Radeon R2 Graphics
/0/17/18                               memory         256KiB L1 cache
/0/17/19                               memory         2MiB L2 cache
/0/100                                 bridge         Advanced Micro Devices, Inc. [AMD]
/0/100/1                               display        Mullins [Radeon R3 Graphics]
/0/100/1.1                             multimedia     Kabini HDMI/DP Audio
/0/100/2.1                             bridge         Family 16h Processor Functions 5:1
/0/100/2.4                             bridge         Family 16h Processor Functions 5:1
/0/100/2.4/0               wlo1        network        RTL8723BE PCIe Wireless Network Adapter
/0/100/2.5                             bridge         Family 16h Processor Functions 5:1
/0/100/2.5/0               enp3s0      network        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
/0/100/8                               generic        Advanced Micro Devices, Inc. [AMD]
/0/100/10                              bus            FCH USB XHCI Controller
/0/100/10/0                usb3        bus            xHCI Host Controller
/0/100/10/0/2              scsi2       storage        USB Flash Disk
/0/100/10/0/2/0.0.0        /dev/sdb    disk           4026MB USB Flash Disk
/0/100/10/0/2/0.0.0/0      /dev/sdb    disk           4026MB 
/0/100/10/0/2/0.0.0/0/2    /dev/sdb2   volume         15EiB Windows FAT volume
/0/100/10/1                usb4        bus            xHCI Host Controller
/0/100/11                              storage        FCH SATA Controller [AHCI mode]
/0/100/12                              bus            FCH USB EHCI Controller
/0/100/12/1                usb1        bus            EHCI Host Controller
/0/100/12/1/1                          bus            USB hub
/0/100/12/1/1/1            scsi3       storage        USB Storage
/0/100/12/1/1/1/0.0.0      /dev/sdc    disk           1029MB STORAGE DEVICE
/0/100/12/1/1/1/0.0.0/0    /dev/sdc    disk           1029MB 
/0/100/12/1/1/1/0.0.0/0/1  /dev/sdc1   volume         981MiB Windows FAT volume
/0/100/12/1/1/4                        communication  Bluetooth Radio
/0/100/13                              bus            FCH USB EHCI Controller
/0/100/13/1                usb2        bus            EHCI Host Controller
/0/100/13/1/1                          bus            USB hub
/0/100/13/1/1/1                        multimedia     HP Webcam
/0/100/14                              bus            FCH SMBus Controller
/0/100/14.2                            multimedia     FCH Azalia Controller
/0/100/14.3                            bridge         FCH LPC Bridge
/0/100/14.7                            generic        FCH SD Flash Controller
/0/101                                 bridge         Advanced Micro Devices, Inc. [AMD]
/0/102                                 bridge         Advanced Micro Devices, Inc. [AMD]
/0/103                                 bridge         Advanced Micro Devices, Inc. [AMD]
/0/104                                 bridge         Advanced Micro Devices, Inc. [AMD]
/0/105                                 bridge         Advanced Micro Devices, Inc. [AMD]
/0/106                                 bridge         Advanced Micro Devices, Inc. [AMD]
/0/107                                 bridge         Advanced Micro Devices, Inc. [AMD]
/0/1                       scsi0       storage        
/0/1/0.0.0                 /dev/sda    disk           128GB SAMSUNG MZNTY128
/0/1/0.0.0/1               /dev/sda1   volume         39MiB Windows FAT volume
/0/1/0.0.0/2               /dev/sda2   volume         400MiB EXT4 volume
/0/1/0.0.0/3               /dev/sda3   volume         119GiB Windows NTFS volume
/0/2                       scsi1       storage        
/0/2/0.0.0                 /dev/cdrom  disk           DVDRW  DU8AESH



```

---

