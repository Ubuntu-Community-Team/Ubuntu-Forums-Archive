---
title: "No option to erase disk and install ubuntu?"
date: 2022-11-25
forum: Installation &amp; Upgrades
---

### Post by mchamplin on 2022-11-25
I have created a boot image on a USB memory stick.

The desktop PC boots up just fine from the USB.

I click on the "Install Ubuntu" and walk through the installation steps.

However, after the "normal installation" step, I do not get an option to "erase disk and install ubuntu" as seen on videos.

Instead, it goes to the "Installation Type" screen, but there are no partitions to select.  The "device for bootloader installation" is /dev/sda

Selecting "Install Now" at this point produces a "No Root File System is Defined" error.  It says to correct this on the partition menu but there are no partitions.

Hence, my installation cannot proceed.

Advice?

---

### Post by tea for one on 2022-11-25
Can you supply more info about your PC?
The system-info script has been designed to help with relevant details.
[https://ubuntuforums.org/showthread.php?t=2475931](https://ubuntuforums.org/showthread.php?t=2475931)

---

### Post by yancek on 2022-11-25
Post more info on the computer as asked above, information such as how old/new the computer is, number of drives, are the drives blank or is there another OS on them and if so, what is it?  What you described often happens with a newer version of windows on the computer which is hibernated.   As to the no root filesystem defined error, you won't be able to do that until you have drives/partitions showing and when you do, it will be the Mount point shown on screen where you select:  /

---

### Post by mchamplin on 2022-11-25
Thank you -

It's an HP pavillion HPE bought in 2018
I've wiped the disk - only the barebones windows (10) OS remains
It has one HDD
The intention was to only have Linux on the machine (not run both W10 and Linux)...but I can be flexible.

Does the drive had to be reformated before it can load Linux?

---

### Post by tea for one on 2022-11-25
> **mchamplin said:**
> Does the drive had to be reformated before it can load Linux?
No, the drive has to be visible before you can install Ubuntu.
Did you notice this in post3?
> What you described often happens with a newer version of windows on the computer which is hibernated
Can you double-check the hibernation status of Windows 10?

---

### Post by mchamplin on 2022-11-25
I rebooted to Windows and checked the power settings.  There is no hibernation option under Power Settings...at least not for this Desktop PC.

At any rate, I am not sure why that would matter - I boot from the USB which launches Ubuntu, not Windows.  There should be no Windows code running at that point.  I am not creating 2 partitions, one for Windows and one for Linux, I just want Linux, and only Linux running on this machine.

What is "post 3"?

---

### Post by mchamplin on 2022-11-25
The big question here is:  why, during the Ubuntu installation, is the option page for "Erase and Install Ubuntu" not showing up?  It's as though it does not see anything to erase.

---

### Post by tea for one on 2022-11-25
> **mchamplin said:**
> What is "post 3"?
If you look in the top right corner of a original post/reply, you will see #1 or #2 or #3 etc.
This is the numerical sequence of the original post and subsequent replies.

Anyway, as you have not provided the system-info details, can you boot into a live session:-
Try Ubuntu
Open a terminal and enter:-
```
sudo parted -l
```
In your reply, please pop the terminal output within code tags for legibility.

---

### Post by mchamplin on 2022-11-25
Rebooting Ubuntu...

I assume you are saying post the output of the "sudo parted -l" command?

---

### Post by tea for one on 2022-11-25
Indeed, I am asking you to post the output of the command [COLOR="#0000FF"]sudo parted -l[/COLOR]
To try and identify your internal disk.

---

### Post by mchamplin on 2022-11-25
Here is the output from the sodu parted -l  command

Model: ATA Hitachi (scsi)
Disk /dev/sda: 2000GB
Section Size: 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start     End         Size      Type         File system Flags
1            1049kb 105Mb    105MB   primary    ntfs            boot
2            106MB   1981GB 1981GB  primary    ntfs
3            1981GB  1982GB  895MB  primary    ntfs            msftres
4            1982GB  2000GB  18.3GB primary    ntfs

Model:  Patriot Memory
Disk /dev/sda: 16.0GB
Section Size: 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start     End         Size      Type         File system Flags
1            1049kB  16.0GB   16.0Gb  primary    fat32         boot, lba

---

### Post by maglin2 on 2022-11-25
> **mchamplin said:**
> I rebooted to Windows and checked the power settings.  There is no hibernation option under Power Settings...at least not for this Desktop PC.

IIRC there is a sort of hidden 'hibernate' called Fast start-up. It is enabled by default (and not easy to find).
Control Panel - Power Options- Choose what power buttons do - Turn on Fast start-up (recommended). You'll probably find it's already ticked as on.
There is also a fast start in bios.
Again IIRC from my last install the recommendation is that both these fast starts should be disabled before installing linux.

---

### Post by tea for one on 2022-11-25
Disk is visible via [COLOR="#0000FF"]sudo parted -l[/COLOR], which is good news.
Have you disabled Fast Start Up (Windows Setting) mentioned in post 12?

---

### Post by mchamplin on 2022-11-25
I still don't quite understand why a windows configuration would impact booting Ubuntu from the USB, but anyway...

I booted back up into windows, unchecked the "Fast Start Up" option and rebooted back from the USB (Unbuntu).

Walking through the installation, I still don't see the "Erase disk and install Unbuntu".

---

### Post by ubfan1 on 2022-11-25
With msdos partition tables, only four primary partitions are allowed, and you show four already.  Not sure what the installer can do in that situation except erase everything. You need to get an extended partition, make one of the existing ones an extended and add logical parrtitions there.

---

### Post by mchamplin on 2022-11-25
These partitions were established for Windows.  

Shouldn't the disk be formatted for Linux (Ext4 partition)?  Is there a way to download and run an app on Ubuntu to format the disk the way the Ubuntu HD installation needs?  I have no need for these existing four partitions.

I never did anything unique or fancy to my PC/Windows/File System set up.  When I bought it, I just fired it up out of the box, added apps along the way, and that was it.  It's hard to believe no one has ever come across this same issue while installing Linux.

---

### Post by ubfan1 on 2022-11-25
At the installer page for selecting the installation type, choose "something else".  Under that, you can select the disk, delete partitions, change partition type to gpt(so you are not limited to four primary partitions).  Probably delete all the existing partitions, create a new gpt partition table, then add 1)300MB EFI FAT partition 2) 50MB ext4 used as / (root), optional swap, although these days a swap file will be automatically made if you don't, and the rest an ext4 data partition for your files. (or just /home if you don't have multiple installs).  If room, I prefer to make two root partitions so I can install the next release while the old one is still available.

---

### Post by mchamplin on 2022-11-25
Herein lies the main problem.  After clicking on "normal installation", the installation app skips right over the page that gives options to "delete disk and install" or "something else" and goes right to the page that lists the partitions.  But there are no partitions in the list.  None.  Click "Install" on that page anyway just produces the "No Root File System..." error.  

Somehow, I need to get the installer to offer up the "delete disk and install" page/option which means I probably need to do something to the HD to get the installer to see it...ugh

I hope there is a solution to this somewhere because I can't live on the "try it" USB version of Linux/Ubuntu and I really don't want to go back to windows

---

### Post by ubfan1 on 2022-11-25
Sounds like you have no partitions.  You click on the + to add a partition, but I'm not sure if the "change partition type" from msdos to gpt is offered. You can always run the "Try" mode and then  run gparted and achange the partition type to gpt.

---

### Post by mchamplin on 2022-11-26
When I run [COLOR=#000000]sodu parted -l (see post #11), it shows partitions.

But when the install page comes up with the partition table, it shows none.

And, on that page, nothing works - not the +, -, or the "Install Now".[/COLOR]

---

### Post by tea for one on 2022-11-26
> You can always run the "Try" mode and then run gparted and achange the partition type to gpt. 
In post 19, it was suggested to use Gparted before starting the installer.

Boot into Ubuntu live session in UEFI mode.
Select Try Ubuntu
Open Gparted (which is parted with [COLOR="#0000FF"]G[/COLOR]uided [COLOR="#0000FF"]U[/COLOR]ser [COLOR="#0000FF"]I[/COLOR]nterface).
Hopefully, the existing partitions are visible?
If partitions are active (i.e.mounted), unmount all partitions with right click > Unmount
Device > Create Partition Table > Select GPT

Be aware that this is destructive and will delete all existing partitions.
if you are unfamiliar with this procedure, you could practise with another USB stick as a target device.

Then start the installation and see if [COLOR="#0000FF"]Erase and Install Ubuntu[/COLOR] is available.

---

### Post by TheFu on 2022-11-26
> **mchamplin said:**
> I still don't quite understand why a windows configuration would impact booting Ubuntu from the USB, but anyway...
 

Ubuntu is used and installed by people of all skill levels.  When a file system/partition is hibernated, which is the default for MS-Windows, then Linux won't touch it. Period. It is a safety thing.  There are many ways to fix this, but the normal way is to have MS-Windows release the hibernation lock.  Another method would be to use the "Try Ubuntu" method (aka "Live Boot") and any partitioning tool - fdisk, gdisk, parted, gparted ... there are others .... to wipe the partition table, create a new GPT and then run the "Install Ubuntu" from the "Live boot" environment.

Imagine, if you will, that someone unfamiliar with computers was using a "Try Ubuntu" environment and accidentally clicked on the "Install" icon.  It happens all the time.  And people doing this wipe their MS-Windows environment unintentionally.  They come here looking for the "undo" key, only to be disappointed and mad.  Their OS and data are gone.  Extra protection seems to be a good thing, though frustrating to people who don't know these things, I suppose.

But if you'd followed instructions from Post #3, ran the information gathering script and provided the link for others to see, we'd have been passed all this many posts ago.  Linux and all Unix systems require an attention to detail to achieve happiness.  I fear you will be frustrated.  There are many details to know.

---

### Post by mchamplin on 2022-11-26
the partitions are not listed.

I have tried change the device to ext4, but that did not help.  Plus, changed to GPT.

I tried create partition table...and that wiped out the HD, but did not help the installation.

---

### Post by mchamplin on 2022-11-26
It was in Post #2, but I did find it.  Must have overlooked it earlier.  Here is the system-info.txt file from that dump:

```
Starting the Ubuntu Forums 'system-info' Report: 2022-11-27  02:16:02 UTC (+0000)
    Part of the Ama-gi Project
    Version: 02.00-03, Script Date: 2022.10.29

---------------------------------------------------------------
Main Complaint: Install no option to erase disk and install Ubuntu
Problem Description:  Walking through the Install Ubuntu, it skips the page which provides an option to erase disk and install unbuntu.  It goes to the partition table and none are listed.  The device is /dev/sda
---------- General Computer Specifications:

  --- Computer/CPU Information from 'lshw -C cpu' --- 
*-Cpu
    Description: CPU
    Product: AMD FX(tm)-8100 Eight-Core Processor
    Vendor: Advanced Micro Devices [AMD]
    Physical id: 4
    Bus info: cpu@0
    Version: 21.1.2
    Slot: CPU 1
    Size: 1448MHz
    Capacity: 2800MHz
    Width: 64 bits
    Clock: 200MHz
    Capabilities: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 
        apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht 
        syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 constant_tsc rep_good 
        nopl nonstop_tsc cpuid extd_apicid aperfmperf pni pclmulqdq monitor 
        ssse3 cx16 sse4_1 sse4_2 popcnt aes xsave avx lahf_lm cmp_legacy svm 
        extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop 
        skinit wdt fma4 nodeid_msr topoext perfctr_core perfctr_nb cpb 
        hw_pstate ssbd ibpb vmmcall arat npt lbrv svm_lock nrip_save tsc_scale 
        vmcb_clean flushbyasid decodeassists pausefilter pfthreshold lwp 
        cpufreq
    Configuration: cores=8 enabledcores=8 microcode=100664894 
        threads=8

computer
    Description: Desktop Computer
    Product: h8-1220 (QW694AA#ABA)
    Vendor: Hewlett-Packard
    Serial: [REMOVED]
    Width: 64 bits
    Capabilities: smbios-2.7 dmi-2.7 smp vsyscall32
    Configuration:
        boot=normal
        chassis=desktop
        family=103C_53316J
        G=D
        sku=QW694AA#ABA
        uuid=[REMOVED]

------------------ SMBIOS Information from '/sys/class/dmi/id/' 
Bios Vendor:         AMI
Bios Version:        Ang_713
Bios Release:        4.6
Board Vendor:        Gigabyte
Board Name:          2AC8
Board Version:       1.2
Board Serial:        
Board Asset Tag:     

Current boot mode:   UEFI Firmware mode
   --- SecureBoot Status from 'mokutil':
This system doesn't support Secure Boot


---------- Memory Information:
               total        used        free      shared  buff/cache   available
Mem:            7791        1194        1544         197        5051        6135
Swap:              0           0           0

---------- Swap Information:
  --- Info from 'fstab'


  --- Info from '/proc/swaps'
Filename                Type        Size        Used        Priority

  --- System Swapiness Settings
Valid swappiness settings are from 10 - 60 . 
Current setting in '/proc/sys/vm/swappiness': 60 
Current configuration setting in '/etc/sysctl.conf file: 


---------- IP Address Information:
  --- IP Address Information from 'ip addr' --- 
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    inet [REMOVED]
    inet6 [REMOVED]
2: enp7s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
3: wlp6s0b1: <BROADCAST,MULTICAST> mtu 1500 qdisc mq state DOWN group default qlen 1000
    inet [REMOVED]
    inet6 [REMOVED]
    inet6 [REMOVED]
4: wlx20aa4bec00bc: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    inet [REMOVED]
    inet6 [REMOVED]
    inet6 [REMOVED]
    inet6 [REMOVED]
    inet6 [REMOVED]

  --- Internet Connection Status from 'ping [various addresses]' --- 
Connected to Internet with DNS

  --- Network Device Status Summary from 'ip addr' ---  
These Network Devices are up:
4: wlx20aa4bec00bc: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000

For more detailed wireless information, get and run the script at [https://github.com/UbuntuForums/wireless-info](https://github.com/UbuntuForums/wireless-info) 

  --- Hostname from 'hostname --fqdn' ---  
The 'Hostname' of the computer system is: ubuntu


---------- Storage Controller Information From 'lspci':
00:11.0 RAID bus controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [RAID5 mode] (rev 40)
    Subsystem: Hewlett-Packard Company SB7x0/SB8x0/SB9x0 SATA Controller [RAID5 mode]
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 19, NUMA node 0
    I/O ports at f040 [size=8]
    I/O ports at f030 [size=4]
    I/O ports at f020 [size=8]
    I/O ports at f010 [size=4]
    I/O ports at f000 [size=16]
    Memory at feb0b000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [70] SATA HBA v1.0
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: ahci
    Kernel modules: ahci


---------- File system specs from 'df -h':
Filesystem     Type     Size  Used Avail Use% Mounted on
/dev/sdb1      vfat      15G  3.6G   12G  24% /cdrom
/cow           overlay  3.9G  186M  3.7G   5% /

---------- Disk/Partition Information From 'fdisk':

Disk /dev/sda: 1.82 TiB, 2000398934016 bytes, 3907029168 sectors
Disk model: Hitachi HDS72302
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/sdb: 14.92 GiB, 16018046976 bytes, 31285248 sectors
Disk model: Patriot Memory  
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000908ae

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1  *     2048 31285247 31283200 14.9G  c W95 FAT32 (LBA)


---------- Disk/Partition Information From 'lsblk':
NAME     SIZE FSTYPE   LABEL       MOUNTPOINT                         MODEL
loop0    2.1G squashfs             /rofs                              
sda      1.8T ext4                                                    Hitachi HDS723020BLA642
sdb     14.9G                                                         Patriot Memory
|_sdb1  14.9G vfat     UBUNTU 22_0 /cdrom                             
sdc        0B                                                         SD/MMC
sdd        0B                                                         Compact Flash
sde        0B                                                         SM/xD-Picture
sdf        0B                                                         MS/MS-Pro
sr0     1024M                                                         hp CDDVDW SH-216ALN
   ------- 'lsblk' information continued ...
NAME   HOTPLUG PARTUUID                             UUID
sda          0                                      696ae454-feee-4cae-904b-61804b0731dd
sdb          1                                      
|_sdb1       1 000908ae-01                          0E09-16F0
sdc          1                                      
sdd          1                                      
sde          1                                      
sdf          1                                      
sr0          1                                      

---------- Mount Details of '/etc/fstab':
overlay / overlay rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

---------- Current Mount Details of 'mount':
/dev/loop0 on /rofs type squashfs (ro,noatime,errors=continue)
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)

For more detailed disk Information, please run the 'boot-info' script 
from: (STABLE) [https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair](https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair) 

---------- USB Information from 'lsusb -t -v':
/:  Bus 09.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 5000M
    ID 1d6b:0003 Linux Foundation 3.0 root hub
/:  Bus 08.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub
/:  Bus 07.Port 1: Dev 1, Class=root_hub, Driver=ohci-pci/4p, 12M
    ID 1d6b:0001 Linux Foundation 1.1 root hub
    |__ Port 1: Dev 2, If 0, Class=Wireless, Driver=btusb, 12M
        ID 0a5c:217d Broadcom Corp. HP Bluethunder
    |__ Port 1: Dev 2, If 1, Class=Wireless, Driver=btusb, 12M
        ID 0a5c:217d Broadcom Corp. HP Bluethunder
    |__ Port 1: Dev 2, If 2, Class=Vendor Specific Class, Driver=, 12M
        ID 0a5c:217d Broadcom Corp. HP Bluethunder
    |__ Port 1: Dev 2, If 3, Class=Application Specific Interface, Driver=, 12M
        ID 0a5c:217d Broadcom Corp. HP Bluethunder
/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=ohci-pci/2p, 12M
    ID 1d6b:0001 Linux Foundation 1.1 root hub
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=ohci-pci/5p, 12M
    ID 1d6b:0001 Linux Foundation 1.1 root hub
    |__ Port 2: Dev 2, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
        ID 04f2:1060 Chicony Electronics Co., Ltd 
    |__ Port 2: Dev 2, If 1, Class=Human Interface Device, Driver=usbhid, 1.5M
        ID 04f2:1060 Chicony Electronics Co., Ltd 
    |__ Port 3: Dev 3, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
        ID 192f:0416 Avago Technologies, Pte. ADNS-5700 Optical Mouse Controller (3-button)
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=ohci-pci/5p, 12M
    ID 1d6b:0001 Linux Foundation 1.1 root hub
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/4p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub
    |__ Port 2: Dev 3, If 0, Class=Mass Storage, Driver=usb-storage, 480M
        ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/5p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub
    |__ Port 4: Dev 4, If 0, Class=Vendor Specific Class, Driver=brcmfmac, 480M
        ID 13b1:0039 Linksys AE1200 802.11bgn Wireless Adapter [Broadcom BCM43235]
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/5p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub
    |__ Port 1: Dev 2, If 0, Class=Mass Storage, Driver=usb-storage, 480M
        ID 13fe:3600 Kingston Technology Company Inc. flash drive (4GB, EMTEC)

---------- Video Details from 'lshw':

  *-display
       description: VGA compatible controller
       product: Cedar [Radeon HD 5000/6000/7350/8350 Series]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: /dev/fb0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=radeon latency=0 resolution=1920,1080
       resources: 
           irq:42 
           memory:c0000000-cfffffff 
           memory:fea20000-fea3ffff 
           ioport:e000(size=256) 
           memory:c0000-dffff

   --- Graphics Environment Continued from 'various graphics ENVs' ----
The Current Configured Destop is: ubuntu:GNOME 
The Current Desktop Session is: ubuntu 
The Current X Desktop Information Details from 'xrandr' are: 
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
HDMI-0 disconnected (normal left inverted right x axis y axis)
DVI-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 531mm x 299mm
VGA-0 disconnected (normal left inverted right x axis y axis)
The Current Session Type is: x11 
The Current Display Manager is: gdm3
The Current Desktop Theme: 'Yaru'
The Current Virtual TTY's being used are:
    TTY#    Used By
    tty2    gdm-x-session
    tty2    Xorg
    tty2    gnome-session-b
    pts/0    bash
    pts/0    system-info
    pts/0    system-info
    pts/0    sed
    pts/0    system-info
    pts/0    ps
    pts/0    awk

---------- Sound Device Information From 'lspci':
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
    Subsystem: Hewlett-Packard Company SBx00 Azalia (Intel HDA)
    Flags: bus master, slow devsel, latency 32, IRQ 16, NUMA node 0
    Memory at feb00000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel


01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cedar HDMI Audio [Radeon HD 5400/6300/7300 Series]
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Cedar HDMI Audio [Radeon HD 5400/6300/7300 Series]
    Flags: bus master, fast devsel, latency 0, IRQ 44, NUMA node 0
    Memory at fea40000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [150] Advanced Error Reporting
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel


For more detailed audio information, get and run the script at: [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) 

---------- Repository Information from '/etc/apt/sources.list and etc/apt/sources.list.d/':

Sources List:
deb cdrom:[Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1)]/ jammy main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jammy main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jammy-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jammy-updates main restricted

Sources List from SourcesD:

---------- KeyMap and Locale Information from from various sources:
   --- Keymap Info from 'setxkbmap' ----
rules:      evdev
model:      pc105
layout:     us

   --- Locale Info from 'localectl' ----
   System Locale: LANG=C.UTF-8
       VC Keymap: n/a
      X11 Layout: us
       X11 Model: pc105

---------- Other Details from 'Various':
The current kernel version is:       5.15.0-43-generic 
    --- Operating System Release Description --- 
The current release description is:  Ubuntu 22.04.1 LTS 

Original Installation Date:          2022-11-27+01:59:31 
The Installer log directory exists, but the Installer log files have been removed.
This system may have been installed from a distribution  image file.
Do-Release-Upgrade Date: This system may have not had a 'Release Upgrade' through 'do-release-upgrade'

   --- Hardware Enablement Stack (HWE) Informationt:
These are the current kernel ranges for HWE kernels for this release.
   --- HWE Kernel Reference from 'apt-cache show':
For HWE Package: linux-image-generic-hwe-22.04, Kernel Version: 5.15.0.53.53
For HWE Package: linux-image-generic-hwe-22.04, Kernel Version: 5.15.0.43.44
For HWE Package: linux-image-generic-hwe-22.04, Kernel Version: 5.15.0.25.27

   --- HWE Package Status from 'dpkg':
Package linux-generic-hwe-22.04 is installed.

   --- Certified Hardware Platform Status: (By the Ubuntu Wiki Standards)
Ubuntu Certified Hardware Platform. Safe to install 
the Hardware Enablement Stack (HWE).

   --- User Installed Package List:
adcli
base-passwd
bsdutils
btrfs-progs
casper
cifs-utils
cryptsetup
cryptsetup-bin
cryptsetup-initramfs
dash
dctrl-tools
diffutils
dmeventd
dmraid
dpkg-repack
efibootmgr
findutils
fonts-arphic-ukai
fonts-arphic-uming
fonts-indic
gir1.2-timezonemap-1.0
gir1.2-xkl-1.0
gnome-user-docs-de
gnome-user-docs-es
gnome-user-docs-fr
gnome-user-docs-it
gnome-user-docs-pt
gnome-user-docs-ru
gnome-user-docs-zh-hans
gparted
gparted-common
grep
grub-common
grub-efi-amd64-bin
grub-efi-amd64-signed
grub-gfxpayload-lists
grub-pc
grub-pc-bin
grub2-common
gtk-im-libthai
gzip
hostname
hunspell-fr
hyphen-de
hyphen-en-ca
hyphen-en-gb
hyphen-en-us
hyphen-es
hyphen-fr
hyphen-it
hyphen-pt-br
hyphen-pt-pt
hyphen-ru
ibus-chewing
ibus-hangul
ibus-libpinyin
ibus-m17n
ibus-mozc
ibus-table-cangjie
ibus-table-cangjie-big
ibus-table-cangjie3
ibus-table-cangjie5
ibus-table-quick-classic
ibus-table-wubi
ibus-unikey
init
jfsutils
keyutils
kpartx
kpartx-boot
language-pack-de
language-pack-de-base
language-pack-en
language-pack-en-base
language-pack-es
language-pack-es-base
language-pack-fr
language-pack-fr-base
language-pack-gnome-de
language-pack-gnome-de-base
language-pack-gnome-en
language-pack-gnome-en-base
language-pack-gnome-es
language-pack-gnome-es-base
language-pack-gnome-fr
language-pack-gnome-fr-base
language-pack-gnome-it
language-pack-gnome-it-base
language-pack-gnome-pt
language-pack-gnome-pt-base
language-pack-gnome-ru
language-pack-gnome-ru-base
language-pack-gnome-zh-hans
language-pack-gnome-zh-hans-base
language-pack-it
language-pack-it-base
language-pack-pt
language-pack-pt-base
language-pack-ru
language-pack-ru-base
language-pack-zh-hans
language-pack-zh-hans-base
libaio1
libchewing3
libchewing3-data
libdebconfclient0
libdebian-installer4
libdevmapper-event1.02.1
libdmraid1.0.0.rc16
libdpkg-perl
libfile-fcntllock-perl
libhangul-data
libhangul1
liblvm2cmd2.03
libm17n-0
libmarisa0
libnvpair3linux
libopencc-data
libopencc1.1
libotf1
libpinyin-data
libpinyin13
libreoffice-help-common
libreoffice-help-de
libreoffice-help-en-gb
libreoffice-help-en-us
libreoffice-help-es
libreoffice-help-fr
libreoffice-help-it
libreoffice-help-pt
libreoffice-help-pt-br
libreoffice-help-ru
libreoffice-help-zh-cn
libreoffice-help-zh-tw
libreoffice-l10n-de
libreoffice-l10n-en-gb
libreoffice-l10n-en-za
libreoffice-l10n-es
libreoffice-l10n-fr
libreoffice-l10n-it
libreoffice-l10n-pt
libreoffice-l10n-pt-br
libreoffice-l10n-ru
libreoffice-l10n-zh-cn
libreoffice-l10n-zh-tw
libtimezonemap-data
libtimezonemap1
libuutil3linux
libzfs4linux
libzpool5linux
linux-generic-hwe-22.04
login
lvm2
m17n-db
mokutil
mozc-data
mozc-server
mythes-de
mythes-de-ch
mythes-en-au
mythes-en-us
mythes-es
mythes-fr
mythes-it
mythes-pt-pt
mythes-ru
ncurses-base
ncurses-bin
os-prober
python3-icu
python3-pam
rdate
realmd
reiserfsprogs
shim-signed
thin-provisioning-tools
thunderbird-locale-de
thunderbird-locale-en
thunderbird-locale-en-gb
thunderbird-locale-en-us
thunderbird-locale-es
thunderbird-locale-es-ar
thunderbird-locale-es-es
thunderbird-locale-fr
thunderbird-locale-it
thunderbird-locale-pt
thunderbird-locale-pt-br
thunderbird-locale-pt-pt
thunderbird-locale-ru
thunderbird-locale-zh-cn
thunderbird-locale-zh-hans
thunderbird-locale-zh-hant
thunderbird-locale-zh-tw
ubiquity
ubiquity-casper
ubiquity-frontend-gtk
ubiquity-slideshow-ubuntu
ubiquity-ubuntu-artwork
ubuntu-desktop
ubuntu-desktop-minimal
ubuntu-minimal
ubuntu-standard
ubuntu-wallpapers
xfsprogs
zfs-initramfs
zfs-zed
zfsutils-linux
zsys

   --- Installed Snap Package List:
bare
core20
firefox
gnome-3-38-2004
gtk-common-themes
snap-store
snapd
snapd-desktop-integration

   --- Installed Flatpak Package List:
Flatpak is not installed

Currently logged in User(s):
NAME     LINE         TIME         COMMENT
ubuntu   :0           Nov 27 01:59 (:0)

The User running this script was: ubuntu
uid=999(ubuntu)
gid=999(ubuntu)
groups=999(ubuntu),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),
122(lpadmin),134(lxd),135(sambashare)

The 'system-info' script was booted from a Live Image Environment (LIE).

The 'system-info' script seems to be running locally

The Linux Kernel Command Line use to boot was: 
BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed maybe-ubiquity quiet splash ---

---- Required Programs For Report.
    --- Some Programs This Script Uses Were Missing --- 
    curl
    pastebinit
```

---

### Post by tea for one on 2022-11-27
```
---------- Disk/Partition Information From 'fdisk':

Disk /dev/sda: 1.82 TiB, 2000398934016 bytes, 3907029168 sectors
Disk model: Hitachi HDS72302
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/sdb: 14.92 GiB, 16018046976 bytes, 31285248 sectors
Disk model: Patriot Memory  
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
[COLOR="#0000FF"]Disklabel type: dos[/COLOR]
Disk identifier: 0x000908ae

```
Your Hitachi disk (1.82 TiB) does not have Disklabel type i.e. partition table missing.
For comparison, you can see where I have highlighted in blue the Disklabel of your USB stick.

---

### Post by TheFu on 2022-11-27
```

00:11.0 RAID bus controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [RAID5 mode] (rev 40)
    Subsystem: Hewlett-Packard Company SB7x0/SB8x0/SB9x0 SATA Controller [**RAID5 mode**]
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 19, NUMA node 0
    I/O ports at f040 [size=8]
    I/O ports at f030 [size=4]
    I/O ports at f020 [size=8]
    I/O ports at f010 [size=4]
    I/O ports at f000 [size=16]
    Memory at feb0b000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [70] SATA HBA v1.0
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: **ahci**
    Kernel modules: ahci

```
Just a guess, but it appears you have the MB Fake-RAID enabled.  If true, them please disable that and put it into AHCI mode.  BTW, seems the claims that a new GPT was created didn't actually work out that way.

Here's what a data-only disk here looks like .... with GPT:
```
$ sudo parted -l
Model: ATA Hitachi HDP72505 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
**Partition Table: gpt**
Disk Flags: 

Number  Start   End    Size   File system  Name      Flags
 1      1049kB  500GB  500GB               vg-hadar  lvm
```

---

### Post by tea for one on 2022-11-27
> **mchamplin said:**
> However, after the "normal installation" step, I do not get an option to "erase disk and install ubuntu" as seen on videos.
Instead, it goes to the "Installation Type" screen, but there are no partitions to select.  
I've just re-read your original post and something is not quite right.
You mention that you arrive at the screen "Installation Type", this is the page where you see "Erase Disk and Install Ubuntu"

Drive management from this tutorial [https://ubuntu.com/tutorials/install-ubuntu-desktop#6-drive-management](https://ubuntu.com/tutorials/install-ubuntu-desktop#6-drive-management)

---

