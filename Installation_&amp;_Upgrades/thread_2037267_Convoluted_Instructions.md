---
title: "Convoluted Instructions"
date: 2012-08-04
forum: Installation &amp; Upgrades
---

### Post by KenjaminK on 2012-08-04
I'm trying to install a driver and I'm lost on how to install it. Here are the instructions. There are two sets and I'm not sure which to follow. My base understanding is simply to lacking to handle all of this without proper sentence structure and more thorough steps. It's a wireless adapter, so can you also make sure none of the steps rely on the internet because I'll need to download everything that's missing and have it read beforehand. I'm not dumb, so too much detail isn't required, I just need these instructions to be more clear/help understanding them because I've never had to install a driver by hand before. Usually they come with installers with Windows. Thanks so much for any help! It's greatly appreciated as I'd like to get this done so I can finish setting up the system.

[QUOTE=Quick Start.txt]
RT3573 Linux Driver quick start		

====================
Check tools:  

====================
*Before install driver, please check already install compile tool and  kernel source code

1>Install compile tool
    $yum install gcc-c++

2>check kernel source code exists /usr/src/kernels/ "kernel name"

    Download your kernel source code
    *[http://www.kernel.org/pub/linux/kernel/](http://www.kernel.org/pub/linux/kernel/) 		
	or
    $yum install kernel-devel



====================
Build Instructions:  

====================
1> $tar -jxvf DPA_RT3573_LinuxSTA_V2.5.0.0.bz2
     go to "DPA_RT3573_LinuxSTA_vx.x.x.x" directory.
    


2> In Makefile
	 
     set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
	 
     define the linux kernel source include file path LINUX_SRC
	 
     modify to meet your need.


3> $make			
	
     # compile driver source code, need administrator.
	
     # To fix "error: too few arguments to function ¡¥iwe_stream_add_event"
	 
        => $patch -i os/linux/sta_ioctl.c.patch os/linux/sta_ioctl.c

4>go  MODULE folder
    $make install

5>
    $insmod UTIL/os/linux/rtutil3573sta.ko
    $ insmod MODULE/os/linux/rt3573sta.ko
    $ insmod NETIF/os/linux/rtnet3573sta.ko

6>$ifconfig ra0 up

7> unload driver    
    
     $ifconfig ra0 down

     $rmmod rtnet3573sta.ko
     $rmmod rt3573sta.ko
     $rmmod rtutil3573sta.ko
[/QUOTE]

[QUOTE=Quick Start DPO.txt]
RT3753 Linux Driver quick start		

====================
Check tools:  

====================
*Before install driver, please check already install compile tool and  kernel source code

1>Install compile tool
    $yum install gcc-c++

2>check kernel source code exists /usr/src/kernels/ "kernel name"

    Download your kernel source code
    *[http://www.kernel.org/pub/linux/kernel/](http://www.kernel.org/pub/linux/kernel/) 		
	or
    $yum install kernel-devel



====================
Build Instructions:  

====================
1> $tar -jxvf DPO_RT3573_LinuxSTA_vx.x.x.x.tar.bz2
     go to "DPO_RT3573_LinuxSTA_vx.x.x.x" directory.
    


2> In Makefile
	 
     set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
	 
     define the linux kernel source include file path LINUX_SRC
	 
     modify to meet your need.


3> In os/linux/config.mk 
	
     define the GCC and LD of the target machine
	
     define the compiler flags CFLAGS
	
     modify to meet your need.
     ** Build for being controlled by NetworkManager or wpa_supplicant wext functions
	   
         Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
	   	   
         => $wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d
     ** Build for being controlled by WpaSupplicant with Ralink Driver
	   
         Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
	   
         => $wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d

4> $make			
	
     # compile driver source code, need administrator.
	
     # To fix "error: too few arguments to function ¡¥iwe_stream_add_event"
	 
        => $patch -i os/linux/sta_ioctl.c.patch os/linux/sta_ioctl.c

5> $make install
     #install driver
     #copy RT2870STA.dat to /etc/Wireless/RT2870STA/RT2870STA.dat

6>$vi /etc/rc.d/rc.local
     #input "ifconfig ra0 up"
    $reboot

7> unload driver    
    
     $ifconfig ra0 down

     $make uninstall
     $reboot


Note: If you want to change os/linux/config.mk setting, please remove driver and  reinstall.
[/QUOTE]

Again, thanks! :)

---

### Post by cwsnyder on 2012-08-04
First off, your problems may be that the instructions are for a OpenSUSE/Fedora based distribution instead of a Debian/Ubuntu based system, which may have caused you some difficulty.

Second, You do realize that you are modifying the kernel on your Linux install and that any kernel updates will require you to re-modify the kernel again after downloading the (new) kernel source?

If after reading the above, you still wish to attempt the project, see the instructions and warnings at [https://help.ubuntu.com/community/Kernel/Compile/](https://help.ubuntu.com/community/Kernel/Compile/)

There is another thread at [http://ubuntuforums.org/showthread.php?t=1329254](http://ubuntuforums.org/showthread.php?t=1329254) discussing the same problem from a few years back.

---

### Post by robert shearer on 2012-08-04
If you could supply some details.....
what version of Ubuntu are you using.
 What model wireless interface are you trying to configure.
and open a terminal then run..
```
sudo lshw
```
and post the results here.  (lshw = list hardware)

then we can advise the best way for you to acheive your desired outcome.... :)

---

### Post by KenjaminK on 2012-08-04
> **cwsnyder said:**
> First off, your problems may be that the instructions are for a OpenSUSE/Fedora based distribution instead of a Debian/Ubuntu based system, which may have caused you some difficulty.

Second, You do realize that you are modifying the kernel on your Linux install and that any kernel updates will require you to re-modify the kernel again after downloading the (new) kernel source?

If after reading the above, you still wish to attempt the project, see the instructions and warnings at [https://help.ubuntu.com/community/Kernel/Compile/](https://help.ubuntu.com/community/Kernel/Compile/)

There is another thread at [http://ubuntuforums.org/showthread.php?t=1329254](http://ubuntuforums.org/showthread.php?t=1329254) discussing the same problem from a few years back.

Well, apparently Ubuntu isn't as viable an OS as I thought. Is there any way to get my wireless adapter working with Ubuntu without some kind of kernel headache or is Ubuntu just incompatible? :confused:

---

### Post by KenjaminK on 2012-08-04
> **robert shearer said:**
> If you could supply some details.....
what version of Ubuntu are you using.
 What model wireless interface are you trying to configure.
and open a terminal then run..
```
sudo lshw
```
and post the results here.  (lshw = list hardware)

then we can advise the best way for you to acheive your desired outcome.... :)

Sure, be back in a second with lshw info, but for the moment the adapter is a Belkin n750 db and I'm on Ubuntu 12.04 LTS

---

### Post by KenjaminK on 2012-08-04
```
kenjamink@ubuntu:~$ sudo lshw
[sudo] password for kenjamink: 
ubuntu                    
    description: Desktop Computer
    product: M68MT-S2 ()
    vendor: Gigabyte Technology Co., Ltd.
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=6 uuid=35304535-3439-3939-3837-3930FFFFFFFF
  *-core
       description: Motherboard
       product: M68MT-S2
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: FB
          date: 08/26/2011
          size: 128KiB
          capacity: 1984KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD FX(tm)-6100 Six-Core Processor
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 3
          bus info: cpu@0
          version: 15.1.2
          slot: Socket M2
          size: 3300MHz
          capacity: 3300MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 constant_tsc nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 cx16 sse4_1 sse4_2 popcnt aes xsave avx lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 nodeid_msr topoext perfctr_core arat cpb npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold cpufreq
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 80KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L3 cache
             physical id: a
             slot: External Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: synchronous internal write-back
     *-cache
          description: L1 cache
          physical id: 4
          slot: Internal Cache
          size: 128KiB
          capacity: 128KiB
          capabilities: synchronous internal write-back
     *-memory:0
          description: System Memory
          physical id: 1e
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: DIMM 1333 MHz (0.8 ns)
             physical id: 0
             slot: A0
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM 1333 MHz (0.8 ns)
             physical id: 1
             slot: A1
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-cpu:1
          physical id: 6
          bus info: cpu@1
          version: 15.1.2
          size: 3300MHz
          capacity: 3300MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 80KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 2MiB
     *-cpu:2
          physical id: 9
          bus info: cpu@2
          version: 15.1.2
          size: 3300MHz
          capacity: 3300MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 80KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 2MiB
     *-cpu:3
          physical id: a
          bus info: cpu@3
          version: 15.1.2
          size: 3300MHz
          capacity: 3300MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 80KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 2MiB
     *-cpu:4
          physical id: b
          bus info: cpu@4
          version: 15.1.2
          size: 3300MHz
          capacity: 3300MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 80KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 2MiB
     *-cpu:5
          physical id: c
          bus info: cpu@5
          version: 15.1.2
          size: 3300MHz
          capacity: 3300MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 80KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 2MiB
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP61 Host Bridge
          vendor: NVIDIA Corporation
          physical id: d
          bus info: pci@0000:00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP61 LPC Bridge
          vendor: NVIDIA Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP61 SMBus
          vendor: NVIDIA Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:5 ioport:fc00(size=64) ioport:1c00(size=64) ioport:1c40(size=64)
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: NVIDIA Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB controller
          product: MCP61 USB 1.1 Controller
          vendor: NVIDIA Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:23 memory:fe02f000-fe02ffff
     *-usb:1
          description: USB controller
          product: MCP61 USB 2.0 Controller
          vendor: NVIDIA Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:fe02e000-fe02e0ff
     *-pci:0
          description: PCI bridge
          product: MCP61 PCI bridge
          vendor: NVIDIA Corporation
          physical id: 100
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
          resources: ioport:b000(size=4096) memory:fdf00000-fdffffff memory:fde00000-fdefffff
     *-multimedia
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: NVIDIA Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=snd_hda_intel latency=0 maxlatency=5 mingnt=2
          resources: irq:22 memory:fe024000-fe027fff
     *-bridge
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: NVIDIA Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: eth0
          version: a2
          serial: 50:e5:49:99:87:90
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
          resources: irq:42 memory:fe02d000-fe02dfff ioport:f000(size=8)
     *-ide:0
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: NVIDIA Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          logical name: scsi0
          logical name: scsi1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:21 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:dc00(size=16) memory:fe02c000-fe02cfff
        *-disk
             description: ATA Disk
             product: ST500DM002-1BC14
             vendor: Seagate
             physical id: 0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: JC4B
             serial: Z2AAXC2X
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=1c4c5efa
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: 04d629e4-c36c-8e45-95d6-49a55db92bd5
                size: 98MiB
                capacity: 100MiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2011-10-10 17:19:21 filesystem=ntfs label=System Reserved state=clean
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /host
                version: 3.1
                serial: aaab8d84-c2ab-cc44-86fd-35753ef8d980
                size: 465GiB
                capacity: 465GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2011-10-10 17:19:22 filesystem=ntfs modified_by_chkdsk=true mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 mounted_on_nt4=true resize_log_file=true state=mounted upgrade_on_mount=true
        *-cdrom
             description: DVD-RAM writer
             product: iHAS124   B
             vendor: ATAPI
             physical id: 1
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: AL0N
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-ide:1
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: NVIDIA Corporation
          physical id: 8.1
          bus info: pci@0000:00:08.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:20 ioport:9e0(size=8) ioport:be0(size=4) ioport:960(size=8) ioport:b60(size=4) ioport:c800(size=16) memory:fe02b000-fe02bfff
     *-pci:1
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: NVIDIA Corporation
          physical id: 101
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:40 ioport:a000(size=4096) memory:fdd00000-fddfffff ioport:d0000000(size=268435456)
        *-display
             description: VGA compatible controller
             product: Turks [Radeon HD 6670]
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 0
             bus info: pci@0000:02:00.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
             configuration: driver=radeon latency=0
             resources: irq:41 memory:d0000000-dfffffff memory:fddc0000-fdddffff ioport:ac00(size=256) memory:fdd00000-fdd1ffff
        *-multimedia
             description: Audio device
             product: Turks HDMI Audio [Radeon HD 6000 Series]
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 0.1
             bus info: pci@0000:02:00.1
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm pciexpress msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:43 memory:fddfc000-fddfffff
     *-pci:2
          description: Host bridge
          product: Family 15h Processor Function 0
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 15h Processor Function 1
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 15h Processor Function 2
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Family 15h Processor Function 3
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 105
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:6
          description: Host bridge
          product: Family 15h Processor Function 4
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 106
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=fam15h_power
          resources: irq:0
     *-pci:7
          description: Host bridge
          product: Family 15h Processor Function 5
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 107
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz
kenjamink@ubuntu:~$ 

```
There we are!

---

### Post by KenjaminK on 2012-08-04
Still trying to figure out whether or not I should give up until I have an ethernet connection available... :confused:

---

### Post by cwsnyder on 2012-08-05
Your RT3573 is NOT listed on your lshw listing.  Did you perform it on the machine you are trying to fix?

---

### Post by robert shearer on 2012-08-05
Ah, curiouser and curiouser...
It's a usb dongle ?  so with it plugged in run..
```
lsusb
```
and report please.

---

### Post by KenjaminK on 2012-08-05
> **cwsnyder said:**
> Your RT3573 is NOT listed on your lshw listing.  Did you perform it on the machine you are trying to fix?
Yes. :confused:

> **robert shearer said:**
> Ah, curiouser and curiouser...
It's a usb dongle ?  so with it plugged in run..
```
lsusb
```
and report please.

```
kenjamink@ubuntu:~$ lsb_release -d
Description:	Ubuntu 12.04 LTS
kenjamink@ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 050d:1103 Belkin Components 
Bus 002 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 002 Device 003: ID 045e:0730 Microsoft Corp. 
kenjamink@ubuntu:~$
```

---

### Post by robert shearer on 2012-08-06
> ID 050d:1103 Belkin Components

Quick search returns...

[https://answers.launchpad.net/ubuntu/+question/145195](https://answers.launchpad.net/ubuntu/+question/145195)
[http://www.linuxforums.org/forum/hardware-peripherals/153511-belkin-wireless-card.html](http://www.linuxforums.org/forum/hardware-peripherals/153511-belkin-wireless-card.html)   
[http://forums.fedoraforum.org/archive/index.php/t-281195.html](http://forums.fedoraforum.org/archive/index.php/t-281195.html)

There may be something there that helps...

---

