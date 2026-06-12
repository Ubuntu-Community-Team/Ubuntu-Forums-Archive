---
title: "Blank DVD will not mount"
date: 2008-08-08
forum: Installation &amp; Upgrades
---

### Post by rcatman on 2008-08-08
I've been having issues regarding my dvd drive on my laptop. It's a dvd/cd writer. 

Here's what I get from **/var/log/syslog**:
> Aug  8 16:38:20 ryan-laptop kernel: [37011.410440] sr0: CDROM (ioctl) error, command: Read TOC/PMA/ATIP 43 00 00 00 00 00 00 00 0c 00
Aug  8 16:38:20 ryan-laptop kernel: [37011.410450] sr: Sense Key : Medium Error [current] 
Aug  8 16:38:20 ryan-laptop kernel: [37011.410453] sr: Add. Sense: Unable to recover table-of-contents
Aug  8 16:38:20 ryan-laptop kernel: [37011.414180] sr0: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00
Aug  8 16:38:20 ryan-laptop kernel: [37011.414186] sr: Sense Key : Medium Error [current] 
Aug  8 16:38:20 ryan-laptop kernel: [37011.414188] sr: Add. Sense: Unable to recover table-of-contents
Aug  8 16:38:20 ryan-laptop kernel: [37011.416453] sr0: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00
Aug  8 16:38:20 ryan-laptop kernel: [37011.416459] sr: Sense Key : Medium Error [current] 
Aug  8 16:38:20 ryan-laptop kernel: [37011.416461] sr: Add. Sense: Unable to recover table-of-contents

Here's my **lspci**:
> 00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
00:06.1 Modem: nVidia Corporation nForce3 Audio (rev a2)
00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go 64M] (rev a3)
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)


Here's my **/etc/fstab**:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=a4bf201a-cc3f-4cd4-b570-eb7249d9d5c5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=0a847189-1732-4da5-b5eb-dd1c887893a8 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


I've been having issues since I upgraded from Gutsy to Hardy. I couldn't mount an audio CD or a data CD containing pictures up until today (maybe an update I did yesterday fixed it). I can mount a video DVD, but my blank dvd is not mounting.

---

### Post by chiefchimp on 2008-08-08
Blank DVDs or CDROMs can't be mounted, you gotta have a filesystem on them before you can mount them

/]/]ik

---

