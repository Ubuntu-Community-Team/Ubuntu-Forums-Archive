---
title: "Installation Lubuntu 19.04"
date: 2019-06-13
forum: Installation &amp; Upgrades
---

### Post by semptoshiro on 2019-06-13
Hi all,

I have been trying to install Lubuntu 19.04 alongside Windows 10 on a laptop that lacks storage capacity.
Running the ISO image on "try" mode and using the Installation option, only the manual partitioning option is available. When I try to do any modification using this option, it says that will create a new partition (free space), but with exact amount that I have free, not used by Windows. I've tried different values for the partitions, but always the same value is fixed (9.2 GB - there is a print screen shot of it).
Could someone help me with that? I'm open also to install just Lubuntu...since Windows 10 with this low capacity is running very slow.
Thanks! :)

---

### Post by &amp;wP*!) on 2019-06-13
On whiich partition is Windows?
Why do you have 2 NTFS? Why is there an NTFS at the end?

---

### Post by Rubi1200 on 2019-06-13
Can we back up a minute because we need more information to help you.

Is this a multimedia card? How did you install Windows?

Does the machine have secure boot or fast startup enabled?

---

### Post by semptoshiro on 2019-06-14
> **pencuse said:**
> On whiich partition is Windows?
Why do you have 2 NTFS? Why is there an NTFS at the end?

Windows is at the biggest partition (19.2 GB). For the NTFS, I don't know. I didn't change anything since I bought this laptop (ASUS - Intel Atom X5-Z8300, 2GB RAM, 32 GB eMMC).

---

### Post by semptoshiro on 2019-06-14
> **Rubi1200 said:**
> Can we back up a minute because we need more information to help you.

Is this a multimedia card? How did you install Windows?

Does the machine have secure boot or fast startup enabled?

No, it's not a multimedia card. Windows was installed when I bought the laptop, so I don't have info about the installation. sorry. :(

Before to try Lubuntu, I disabled both options in BIOS, following the per-installation requirements.

---

### Post by Rubi1200 on 2019-06-14
Here is what I suggest.

Boot the laptop with the Lubuntu live ISO and choose to Try Lubuntu first.

Once you are at the desktop open a terminal with CTRL+ALT+T and then enter these commands:

```
sudo fdisk -l
```

Lowercase L not 1

If you are connected to the internet I would also run the boot info script (see first link in my signature) and only do the summary report, not the repair.

The report will tell us a lot more but if you can only do the first one that is also fine.

Post the information here using code tags please (reply >> go advanced >> look for # symbol and paste text between the tags).

Thanks.

---

### Post by semptoshiro on 2019-06-14
```
Disk /dev/loop0: 1.5 GiB, 1589342208 bytes, 3104184 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mmcblk0: 29.1 GiB, 31268536320 bytes, 61071360 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: B8B86B1A-8003-4E16-8E99-744A40E0F838

Device            Start      End  Sectors  Size Type
/dev/mmcblk0p1     2048   534527   532480  260M EFI System
/dev/mmcblk0p2   534528   567295    32768   16M Microsoft reserved
/dev/mmcblk0p3   567296 60047359 59480064 28.4G Microsoft basic data
/dev/mmcblk0p4 60047360 61069311  1021952  499M Windows recovery environment


Disk /dev/sda: 7.5 GiB, 8004304896 bytes, 15633408 sectors
Disk model: Cruzer Edge     
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0007eb09

Device     Boot Start      End  Sectors  Size Id Type
/dev/sda1  *     2048 15633407 15631360  7.5G  c W95 FAT32 (LBA)


Disk /dev/zram0: 235.3 MiB, 246759424 bytes, 60244 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/zram1: 235.3 MiB, 246759424 bytes, 60244 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/zram2: 235.3 MiB, 246759424 bytes, 60244 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/zram3: 235.3 MiB, 246759424 bytes, 60244 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
```

---

### Post by Rubi1200 on 2019-06-14
So, I am not an expert in this by any means and I am not sure where the 9.2GB free space comes from but...I believe the problem is that the installer is not booted in UEFI mode.

This accounts for the difference between what the installer sees and what fdisk shows.

fdisk is showing a GPT setup and one partition of 28.4GB

You need to boot the USB or DVD whatever you have and go back into BIOS and if there is an option to boot with EFI to then choose the option (more here):
[https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_Ubuntu_DVD_in_UEFI_mode](https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_Ubuntu_DVD_in_UEFI_mode)

There are also options here on how to boot in UEFI mode:
[https://www.tenforums.com/tutorials/21756-boot-usb-drive-windows-10-pc.html](https://www.tenforums.com/tutorials/21756-boot-usb-drive-windows-10-pc.html)

The installer should then see the correct layout and you should then also see the normal options such as Install Alongside etc. and not just manual.

Let us know if this works before actually installing just so we can make sure it will do what you want it to do.

---

### Post by semptoshiro on 2019-06-14
Hi,

thanks for the help. I was struggling to post the other log report. it wasn't possible to past here as code (something about the security token).
in any case, there is the link for the other report here:

[HTML] http://paste.ubuntu.com/p/CnXtXvrjwy/

[/HTML]

I'll try your recommendations and post an update here, before to proceed to the real installation. 

thanks again! :)

---

### Post by semptoshiro on 2019-06-14
Hi,

I think Lubuntu is already booting with EFI, since it's written in front of my boot option: "UEFI: San disk...(my USB flash drive name)".
I'm booting from my BIOS option, so I'm pressing F2 every time that I want to boot Lubuntu. Within my BIOS options, I choose the UEFI option.

Another clarification that maybe is needed: the screenshot that I posted on my first post was a step further of the manual partitioning option, so after selecting the biggest partition and pressing EDIT and trying to shrink the partition (giving me always the same value for FREE SPACE). The initial manual partitioning screen gives me biggest partition with 28.4 GB as the GPT shows (attached).

Thanks again!
cheers,

---

### Post by oldfred on 2019-06-14
Have you considered just installing Ubuntu to an external drive?
Your MMC is small and you have very little room for anything.

---

### Post by tea for one on 2019-06-14
Am I correct in thinking that you have a 32GB MMC soldered drive in a cheap and cheerful netbook?

Windows OS and its Recovery Partitions will take up approx 20-21GB, so your original post where you mention 9.2GB of available free space is correct?

It would be possible to squeeze Lubuntu or Xubuntu Core [https://unit193.net/xubuntu/core/](https://unit193.net/xubuntu/core/) in the free space but you would have very little room for personal data etc.

If you decide to proceed with a Dual Boot, it is often advised to use the Windows tools to shrink the Windows partition.

Before you install anything, have you checked that your wifi, sound, resolution etc. are OK in a Lubuntu live session?

---

### Post by semptoshiro on 2019-06-15
> **oldfred said:**
> Have you considered just installing Ubuntu to an external drive?
Your MMC is small and you have very little room for anything.

Hum...since it's a computer for traveling/using in the train/metro, I will prefer to not use an external drive. That's why I'm also open to replace Windows for Lubuntu.

---

### Post by semptoshiro on 2019-06-15
> **tea for one said:**
> Am I correct in thinking that you have a 32GB MMC soldered drive in a cheap and cheerful netbook?

Windows OS and its Recovery Partitions will take up approx 20-21GB, so your original post where you mention 9.2GB of available free space is correct?

It would be possible to squeeze Lubuntu or Xubuntu Core [https://unit193.net/xubuntu/core/](https://unit193.net/xubuntu/core/) in the free space but you would have very little room for personal data etc.

If you decide to proceed with a Dual Boot, it is often advised to use the Windows tools to shrink the Windows partition.

Before you install anything, have you checked that your wifi, sound, resolution etc. are OK in a Lubuntu live session?

Yes. it's very bad in terms of space. 

Yes. 9.2 is the space left

I'm really considering to replace Windows 10 for Lubunu. Until now everything is working faster and smooth, only the sound is mute still, but I didn't look for drivers, etc. Do you think this could be a problem if I go for a full installation?

---

### Post by tea for one on 2019-06-15
> **semptoshiro said:**
>  Until now everything is working faster and smooth, only the sound is mute still, but I didn't look for drivers, etc. Do you think this could be a problem if I go for a full installation?

Yes, I do consider that sound could be a problem if you proceed with a full installation. Sound is a bit of a pain to troubleshoot. Are you sure that it is not completely muted?

What is the make/model of your device?

I don't have Lubuntu on my pc so I'm not familiar with the sound settings that it uses.

Anyway, here is a suggestion:-

Boot up a live Lubuntu session
Plug in some headphones - recognised?
Install **pavucontrol** (if it is not already present in Lubuntu) to see if there any settings that allow sound to function. (Pavucontrol has more fine tuning)

Good luck

---

### Post by Rubi1200 on 2019-06-15
According to this it should be installed by default:
[https://manual.lubuntu.me/2/2.5/2.5.2/pulseaudio_volume_control.html](https://manual.lubuntu.me/2/2.5/2.5.2/pulseaudio_volume_control.html)

The main manual should be of help in many situations:
[https://manual.lubuntu.me/index.html](https://manual.lubuntu.me/index.html)

---

### Post by semptoshiro on 2019-06-27
Hi all,

As most part of you recommended, before to go for a full installation of Lubuntu, I've been trying to make the sound work....and not being successful until now.
Something that I was wondering: most part of the changes/updates request a reboot. Since I'm running from a flash drive, when I do a reboot, this one effectively counts?

---

### Post by Rubi1200 on 2019-06-28
Any changes made during the live session will be lost when you reboot (unless you set up persistence on the USB).

But if you found a solution that works it should also work on a normal install.

---

### Post by semptoshiro on 2019-06-28
> **Rubi1200 said:**
> But if you found a solution that works it should also work on a normal install.

Yes. That's my problem. I don't know if everything that I've been trying, didn't work until now because I couldn't complete the reboot process. Or do you think isn't crucial to make changes in the sound configuration?

Thanks again!

---

### Post by tea for one on 2019-06-29
You still have not told us the make/model of your device?

Did you plug in some headphones to check if sound is activated?

---

### Post by semptoshiro on 2019-06-30
> **tea for one said:**
> You still have not told us the make/model of your device?

Did you plug in some headphones to check if sound is activated?

I also tried to use headphones, but nothing. :(

```
lubuntu                     
    description: Notebook
    product: E200HA (ASUS-NotebookSKU)
    vendor: ASUSTeK COMPUTER INC.
    version: 1.0
    serial: G3NLCX01U786107
    width: 64 bits
    capabilities: smbios-3.0 dmi-3.0 smp vsyscall32
    configuration: boot=normal chassis=notebook family=E sku=ASUS-NotebookSKU uuid=A934A03F-A73B-4F3D-BF8C-A91D2C4F2CB3
  *-core
       description: Motherboard
       product: E200HA
       vendor: ASUSTeK COMPUTER INC.
       physical id: 0
       version: 1.0
       serial: BSN12345678901234567
       slot: MIDDLE
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: E200HA.207
          date: 02/01/2016
          size: 64KiB
          capacity: 6080KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int14serial int17printer acpi usb smartbattery biosbootspecification uefi
     *-memory
          description: System Memory
          physical id: a
          slot: System board or motherboard
          size: 2GiB
          capabilities: ecc
          configuration: errordetection=multi-bit-ecc
        *-bank:0
             description: DIMM DDR3 1600 MHz (0.6 ns)
             product: Array1_PartNumber0
             vendor: A1_Manufacturer0
             physical id: 0
             serial: A1_SerNum0
             slot: A1_DIMM0
             size: 2GiB
             width: 8 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: DIMM [empty]
             product: Array1_PartNumber1
             vendor: A1_Manufacturer1
             physical id: 1
             serial: A1_SerNum1
             slot: A1_DIMM1
     *-cache:0
          description: L1 cache
          physical id: 11
          slot: CPU Internal L1
          size: 224KiB
          capacity: 224KiB
          capabilities: internal write-back
          configuration: level=1
     *-cache:1
          description: L2 cache
          physical id: 12
          slot: CPU Internal L2
          size: 2MiB
          capacity: 2MiB
          capabilities: internal write-back unified
          configuration: level=2
     *-cpu
          description: CPU
          product: Intel(R) Atom(TM) x5-Z8300  CPU @ 1.44GHz
          vendor: Intel Corp.
          physical id: 13
          bus info: cpu@0
          version: Intel(R) Atom(TM) x5-Z8300 CPU @ 1.44GHz
          size: 572MHz
          capacity: 2400MHz
          width: 64 bits
          clock: 80MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology tsc_reliable nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 movbe popcnt tsc_deadline_timer aes rdrand lahf_lm 3dnowprefetch epb pti tpr_shadow vnmi flexpriority ept vpid tsc_adjust smep erms dtherm ida arat cpufreq
          configuration: cores=4 enabledcores=4 threads=4
     *-pci
          description: Host bridge
          product: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series SoC Transaction Register
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 22
          width: 32 bits
          clock: 33MHz
          configuration: driver=iosf_mbi_pci
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Configuration Registers
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 22
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:128 memory:90000000-90ffffff memory:80000000-8fffffff ioport:f000(size=64) memory:c0000-dffff
        *-generic:0
             description: Signal processing controller
             product: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Power Management Controller
             vendor: Intel Corporation
             physical id: b
             bus info: pci@0000:00:0b.0
             version: 22
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm cap_list
             configuration: driver=proc_thermal latency=0
             resources: irq:131 memory:91639000-91639fff
        *-usb
             description: USB controller
             product: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series USB xHCI Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 22
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:117 memory:91600000-9160ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 5.0.0-13-generic xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 5.00
                capabilities: usb-2.00
                configuration: driver=hub slots=7 speed=480Mbit/s
              *-usb:0
                   description: Video
                   product: USB2.0 VGA UVC WebCam
                   vendor: 04081-0005590015481008276
                   physical id: 1
                   bus info: usb@1:1
                   version: 0.01
                   serial: 200901010001
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
              *-usb:1
                   description: Bluetooth wireless interface
                   vendor: IMC Networks
                   physical id: 3
                   bus info: usb@1:3
                   version: 0.01
                   capabilities: bluetooth usb-1.10
                   configuration: driver=btusb maxpower=100mA speed=12Mbit/s
              *-usb:2
                   description: Mass storage device
                   product: Cruzer Edge
                   vendor: SanDisk
                   physical id: 4
                   bus info: usb@1:4
                   logical name: scsi0
                   version: 1.26
                   serial: 20051739230A0FD2A8FB
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=200mA speed=480Mbit/s
                 *-disk
                      description: SCSI Disk
                      product: Cruzer Edge
                      vendor: SanDisk
                      physical id: 0.0.0
                      bus info: scsi@0:0.0.0
                      logical name: /dev/sda
                      version: 1.26
                      serial: 20051739230A0FD2A8FB
                      size: 7633MiB (8004MB)
                      capabilities: removable
                      configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512
                    *-medium
                         physical id: 0
                         logical name: /dev/sda
                         size: 7633MiB (8004MB)
                         capabilities: partitioned partitioned:dos
                         configuration: signature=0007eb09
                       *-volume
                            description: Windows FAT volume
                            vendor: SYSLINUX
                            physical id: 1
                            logical name: /dev/sda1
                            logical name: /cdrom
                            version: FAT32
                            serial: 6c0d-bc2d
                            size: 7630MiB
                            capacity: 7632MiB
                            capabilities: primary bootable fat initialized
                            configuration: FATs=2 filesystem=fat label=LUBUNTU 19_ mount.fstype=vfat mount.options=ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 5.0.0-13-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 5.00
                capabilities: usb-3.00
                configuration: driver=hub slots=6 speed=5000Mbit/s
        *-generic:1
             description: Encryption controller
             product: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Trusted Execution Engine
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 22
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_txe latency=0
             resources: irq:132 memory:91500000-915fffff memory:91400000-914fffff
        *-pci
             description: PCI bridge
             product: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Express Port #1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 22
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:116 ioport:1000(size=4096) memory:91200000-913fffff ioport:91700000(size=2097152)
           *-network
                description: Wireless interface
                product: QCA9377 802.11ac Wireless Network Adapter
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: wlp1s0
                version: 30
                serial: 80:a5:89:ae:56:bb
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath10k_pci driverversion=5.0.0-13-generic firmware=WLAN.TF.2.1-00021-QCARMSWP-1 ip=192.168.0.157 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:133 memory:91200000-913fffff
        *-isa
             description: ISA bridge
             product: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCU
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 22
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0


```

---

### Post by tea for one on 2019-06-30
I just had a quick search about your ASUS laptop and sound problems with Linux.

It appears that there are many users with similar difficulties, however there are reports that Ubuntu (rather than Lubuntu) users have had better luck although I couldn't find a definitive fix for you.

I suggest that you pop your device **Asus E200HA** in a search engine together with **"Linux sound"** (including the quotation marks) and see if any of the suggestions may help.

---

