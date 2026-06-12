---
title: "Laptop freezes as it wakes up after sleep, reboot needed"
date: 2008-11-19
forum: Installation &amp; Upgrades
---

### Post by monti on 2008-11-19
Hi. I'm running Ubuntu 8.10, and my laptop does not wake up after sleep.

When I close the lid (or press Fn-F2) the laptop goes to standby. The display turns off and the power light starts blinking slowly.

When I wake it from sleep, the power light stays on, but that's it. The display is still off, and the hard drive light does not blink. The laptop doesn't answer to ping or ssh or ctrl-alt-del, and a hard reboot is needed.

The laptop is a Kohjinsha SH-6 (SH6WP10A):

    * Processor: Intel A100 600 MHz processor
    * Motherboard: Intel® 945GU +ICH7U
    * Memory: 1GB DDR2-400 ram
    * HD: 100 GB HDD
    * Screen: 7" LCD screen with a max resolution of 1024×600 or 1600x1200 via the VGA port. (Touch Screen capable)
    * Connectivity: 10BASE-T/100BASE-TX, WLAN IEEE 802.11b/g, Bluetooth Ver 2.0+EDR
    * Audio: Realtek High Definition Audio
    * Camera: 1.3 Mega pixel camera
    * Ports: 2 USB Ports, CF/SD/MMC/MS Input, Wireless On/Off Switch, Audio output and Microphone input

Output from lspci:

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
02:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
02:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
02:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
```
This is the last thing registered in /var/log/messages:

```
Oct 27 19:56:25 headcleaner kernel: [ 219.444303] type=1503 audit(1225133785.515:5): operation="inode_permission" requested_mask="r::" d
enied_mask="r::" fsuid=7 name="/proc/5630/net/" pid=5630 profile="/usr/sbin/cupsd"
Oct 27 19:56:27 headcleaner kernel: [ 221.042620] type=1503 audit(1225133787.111:6): operation="inode_permission" requested_mask="r::" d
enied_mask="r::" fsuid=7 name="/proc/5634/net/" pid=5634 profile="/usr/sbin/cupsd"
Oct 27 19:56:27 headcleaner kernel: [ 221.044393] type=1503 audit(1225133787.115:7): operation="socket_create" family="ax25" sock_type="
dgram" protocol=0 pid=5634 profile="/usr/sbin/cupsd"
Oct 27 19:56:27 headcleaner kernel: [ 221.045759] type=1503 audit(1225133787.115:8): operation="socket_create" family="netrom" sock_type
="seqpacket" protocol=0 pid=5634 profile="/usr/sbin/cupsd"
Oct 27 19:56:27 headcleaner kernel: [ 221.046595] type=1503 audit(1225133787.115:9): operation="socket_create" family="rose" sock_type="
dgram" protocol=0 pid=5634 profile="/usr/sbin/cupsd"
Oct 27 19:56:27 headcleaner kernel: [ 221.051149] type=1503 audit(1225133787.119:10): operation="socket_create" family="ipx" sock_type="
dgram" protocol=0 pid=5634 profile="/usr/sbin/cupsd"
Oct 27 19:56:27 headcleaner kernel: [ 221.055909] type=1503 audit(1225133787.123:11): operation="socket_create" family="appletalk" sock_
type="dgram" protocol=0 pid=5634 profile="/usr/sbin/cupsd"
Oct 27 19:56:27 headcleaner kernel: [ 221.060797] type=1503 audit(1225133787.131:12): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=5634 profile="/usr/sbin/cupsd"
Oct 27 19:56:27 headcleaner kernel: [ 221.065411] type=1503 audit(1225133787.135:13): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=5634 profile="/usr/sbin/cupsd"
Oct 27 19:56:27 headcleaner kernel: [ 221.070000] type=1503 audit(1225133787.139:14): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=5634 profile="/usr/sbin/cupsd"
Oct 27 20:00:08 headcleaner kernel: [ 441.991498] __ratelimit: 3 callbacks suppressedOct 27 20:00:08 headcleaner kernel: [ 441.991518] ACPI: EC: non-query interrupt received, switching to interrupt mode
```

I have reported this in the bugtracker as well: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/290019](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/290019)

---

### Post by SuperBaby on 2009-08-26
I am also using Kohjinsha SH6. I have this problem too. Have you solved it?

---

### Post by monti on 2009-08-26
> **SuperBaby said:**
> I am also using Kohjinsha SH6. I have this problem too. Have you solved it?

Yes!  Install the latest Ubuntu Karmic Alpha and run an update.  Resume works great ([bug 290019]("https://bugs.launchpad.net/pm-utils/+bug/290019/comments/22")), Hibernate still doesn't work ([bug 418850]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418850")).

---

