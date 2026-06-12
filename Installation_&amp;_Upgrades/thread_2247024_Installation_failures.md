---
title: "Installation failures"
date: 2014-10-05
forum: Installation &amp; Upgrades
---

### Post by pandemonium2 on 2014-10-05
[FONT=arial]Hi
I'm new here, and new to Ubuntu. I have always used Windows but had heard good things about this OS so thought I would try it. I just bought a fairly cheap HTPC ([/FONT]Intel BOXDN2820FYKH0 NUC Celeron 2.5" HDD with Gigabit Network) with Intel HD Graphics up to 756 MHz, audio up to 7.1 surround via HDMI interface. I installed Ubuntu via a bootable USB. I'm not a computer genius so perhaps installing this OS was not a good idea, but all seemed to be going well until it came to the audio. Graphics but no audio. I followed the instructions on this thread - [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) . This ultimately resulted in the lttle speaker icon in the top right of the desktop vanishing altogether, and the System Settings icon which appears on the left side of the screen vanishing also. Reinstalled the desktop as I saw suggested on another thread without any cure. 

Now I feel as though I should wipe the installation and put Windows on it, which I will do if you guys think this OS is not for persons of my IT skill(lessness), but I must say I was impressed with Ubuntu - very quick to boot comparitively and much more user friendly than Windows 8.1. Maybe it would be best to get back to where I was when the install was first done and try again? 

Sorry for my first post being report of one major screw up. Usually the way to learn I suppose.

Thanks in advance.

---

### Post by kc1di on 2014-10-05
Hi pandemonium2 and Welcome to Ubuntu,

I personally can not be of much Help but we've all been there and it can be over come at some point by someone on here so be patient.
if you could go to a terminal and post the output of this command it may be of help to those trying diagnose the problem.
```
sudo lshw
```

---

### Post by pandemonium2 on 2014-10-05
Thanks. 
I noter that the thread I followed says it was outdated and gave a link to a much more thorough procedure, which I will follow. I had spent 4 hours trying to fix it, and must have been a little sore in the eyes to have missed that. My major concern atm is to repair the Ubuntu installation, then I'll follow the updated procedure and report if I still have problems - apologies for that. Just in case the terminal command will assist in restoration, I've included the output, which was quite a lot. I've just done a cut and paste for this - sorry about formatting issues: 

home-desktop              
    description: Desktop Computer
    product: &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; (To be filled by O.E.M.)
    vendor: &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
    version: &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
    serial: &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
    width: 64 bits
    capabilities: smbios-2.8 dmi-2.7 ldt16 vsyscall32
     configuration: boot=normal chassis=desktop family=To be filled by  O.E.M. sku=To be filled by O.E.M. uuid=80BBD44D-A653-E211-A482-C03FD564E57E
  *-core
       description: Motherboard
       product: DN2820FYK
       vendor: Intel Corporation
       physical id: 0
       version: H24582-201
       serial: GEFY4160039Y
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 0
          version: FYBYT10H.86A.0015.2013.1210.1722
          date: 12/10/2013
          size: 64KiB
          capacity: 8128KiB
           capabilities: pci upgrade shadowing cdboot bootselect edd  int13floppy1200 int13floppy720 int13floppy2880 int5printscreen  int9keyboard int14serial int17printer acpi usb biosbootspecification  uefi
     *-memory
          description: System Memory
          physical id: 24
          slot: System board or motherboard
          size: 4GiB
        *-bank
             description: SODIMM DDR3 1066 MHz (0.9 ns)
             product: 8KTF51264HZ-1G6E1
             vendor: Micron
             physical id: 0
             serial: D892D689
             slot: SODIMM 0
             size: 4GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
     *-cache:0
          description: L1 cache
          physical id: 2c
          slot: CPU Internal L1
          size: 112KiB
          capacity: 112KiB
          capabilities: internal write-back
     *-cache:1
          description: L2 cache
          physical id: 2d
          slot: CPU Internal L2
          size: 1MiB
          capacity: 1MiB
          capabilities: internal write-back unified
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU  N2820  @ 2.13GHz
          vendor: Intel Corp.
          physical id: 2e
          bus info: cpu@0
          version: Intel(R) Celeron(R) CPU N2820 @ 2.13GHz
          slot: CPU 1
          size: 2128MHz
          capacity: 2400MHz
          width: 64 bits
          clock: 133MHz
           capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce  cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse  sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts  rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64  monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 movbe  popcnt tsc_deadline_timer rdrand lahf_lm 3dnowprefetch ida arat epb  dtherm tpr_shadow vnmi flexpriority ept vpid tsc_adjust smep erms  cpufreq
          configuration: cores=2 enabledcores=2 threads=2
     *-pci
          description: Host bridge
          product: ValleyView SSA-CUnit
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0c
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: ValleyView Gen7
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:107 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:f080(size=8)
        *-storage
             description: SATA controller
             product: ValleyView 6-Port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 0c
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
              resources: irq:104 ioport:f070(size=8) ioport:f060(size=4)  ioport:f050(size=8) ioport:f040(size=4) ioport:f020(size=32)  memory:d0815000-d08157ff
        *-usb
             description: USB controller
             product: ValleyView USB xHCI Host Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:103 memory:d0800000-d080ffff
        *-generic UNCLAIMED
             description: Encryption controller
             product: ValleyView SEC
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:d0500000-d05fffff memory:d0400000-d04fffff
        *-multimedia
             description: Audio device
             product: ValleyView High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:108 memory:d0810000-d0813fff
        *-pci:0
             description: PCI bridge
             product: ValleyView PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:2000(size=4096)
        *-pci:1
             description: PCI bridge
             product: ValleyView PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:3000(size=4096) memory:d0700000-d07fffff
           *-network
                description: Wireless interface
                product: Wireless 7260
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 73
                serial: f8:16:54:6b:ec:70
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-36-generic firmware=22.24.8.0 ip=192.168.0.23 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
                resources: irq:106 memory:d0700000-d0701fff
        *-pci:2
             description: PCI bridge
             product: ValleyView PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:e000(size=4096) memory:d0600000-d06fffff
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 0c
                serial: c0:3f:d5:64:e5:7e
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                 capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet  physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd  autonegotiation
                configuration: autonegotiation=on  broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half  firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes  port=MII speed=10Mbit/s
                resources: irq:105 ioport:e000(size=256) memory:d0604000-d0604fff memory:d0600000-d0603fff
        *-pci:3
             description: PCI bridge
             product: ValleyView PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 ioport:4000(size=4096)
        *-isa
             description: ISA bridge
             product: ValleyView Power Control Unit
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-serial UNCLAIMED
             description: SMBus
             product: ValleyView SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:d0814000-d081401f ioport:f000(size=32)
     *-scsi
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Samsung SSD 840
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: EXT0
             serial: S1D5NSCF427402Y
             size: 111GiB (120GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=f3d2f8e6-6171-4e84-bd65-b7377d9a3873 sectorsize=512
           *-volume:0
                description: Windows FAT volume
                vendor: mkfs.fat
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot/efi
                version: FAT32
                serial: 4543-52b9
                size: 510MiB
                capacity: 511MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /
                version: 1.0
                serial: f6f291e2-ee7d-4323-aaa7-3dfc8da7909d
                size: 107GiB
                 capabilities: journaled extended_attributes large_files huge_files  dir_nlink recover extents ext4 ext2 initialized
                 configuration: created=2014-10-05 16:25:24 filesystem=ext4  lastmountpoint=/ modified=2014-10-05 19:41:24 mount.fstype=ext4  mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-10-05 19:41:24 state=mounted
           *-volume:2
                description: Linux swap volume
                vendor: Linux
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 1
                serial: f1bfda79-2c7c-467f-8503-c29041e52bcc
                size: 3989MiB
                capacity: 3989MiB
                capabilities: nofs swap initialized
                configuration: filesystem=swap pagesize=4095

Thanks

---

### Post by pandemonium2 on 2014-10-05
Hi again. I decided to do a fresh install so booted from USB again. I erased everything and installed again. It got to the end and said it had to restart, which it did and took me back to the original installation choices of trying Ubuntu, installing Ubuntu, or the manufacturer OEM choice. I went to the trying Ubuntu choice, removed the USB and restarted. The computer restarts and tells me in could not find a bootable device. I booted from the USB again, opened a terminal and typed 'sudo fdisk -l'. It gives me two paritions one is '/dev/sda1' which is system type GPT.  The other is '/dev/sdb1' which is system type W93 FAT 32 (LBA). I type in 'sudo grub-install /dev/sda1' It gives me the response 'installing for i386-pc platform   grub-installer:error:failed to get canonical path of /cow'.
I went into the menu from install where I could resize partitions myself just to see what was there and there was 4. Is there away to completely wipe the HD and reinstall as I had no problem with the installation first time?

---

### Post by yancek on 2014-10-05
You should be able to reinstall if you have nothing on the drive you want to save and plan to only use Ubuntu.  The Installation type "Erase disk and install Ubuntu" will do that.  The FAT32 partition is the EFI partition which is used with GPT partitioning which your output shows you have.  I don't use it but my understanding is that you have the option to select UEFI/GPT or MBR options during the installation.  If you select UEFI/GPT then some grub files are installed on the EFI partition.  Not sure what the 4 is you mention, you now have 4 partitions?  Could you boot the installation medium and open a terminal and run:  sudo fdisk -l(Lower Case Letter L in the command) and post that drive/partition information?

---

### Post by pandemonium2 on 2014-10-05
I hit f10 at startup and it gave me the usb and 4 different bootable sectors to choose from. i had installed 4 times, with the erase and install selection each time but it didn't appear to erase properly. None of the boot sectors worked. So I booted to the usb and went into the software and used the partition manager to delete all partitions that I could. Then in the disk utilities I formatted the partition, then reinstalled again. This time the installation went easily as it did first time but the sound didn't work again. I followed the procedure in the first troubleshooting guide in this thread [http://ubuntuforums.org/showthread.php?t=1885240](http://ubuntuforums.org/showthread.php?t=1885240) and ultimately got it working so all is going fantastic now. I expect there was an easier way of achieving this, but happy to have got everything in order. Thanks for any time anyone has put in trying to work this one out. Hopefully I won't be posting with problems again for a good while, but will be back to look at tips etc here.

---

### Post by kc1di on 2014-10-06
Glad you got it working :) 
Enjoy.

---

