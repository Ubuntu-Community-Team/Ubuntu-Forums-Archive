---
title: "Digispark Pro arduino not programming in Linux Mint 18 (Sarah)."
date: 2016-10-20
forum: MINT
---

### Post by rbm0307 on 2016-10-20
Hi,

My question relates to a hardware recognition problem on a variant of Linux that is based on Ubuntu, so I hope that it is not too off.  I've posted this on the Mint forums but no one is able to help there.  I'm hoping I might get an answer here.

I'm trying to install the Arduino IDE on my Thinkpad T430 laptop running Linux Mint 18 (Sarah) but it is failing to recognize and program the **[Digispark Pro](https://www.kickstarter.com/projects/digistump/digispark-pro-tiny-arduino-ready-mobile-and-usb-de)** when I plug it in.  A similar problem was covered in a thread in the Digistump forum, [http://digistump.com/board/index.php/topic,1834.0.html](http://digistump.com/board/index.php/topic,1834.0.html), where that user found a fix on Mint 17 by recompiling the micronucleus.    

I downloaded and installed Arduino IDE v1.6.12 from the official site (as opposed to installing the version available through Software Manager).  I followed the installation instructions on the Digistump wiki, going through the Board Manager.  I selected Digispark Pro (16MHz) but the only port presented by the IDE to me to select was /dev/ttyS4, the native serial port.  I also downloaded and compiled the 2.0a5 micronucleus according to the instructions detailed in the thread above, along with copying the 49-micronucleus.rules into /etc/udev/rules.d/ directory. I've followed advice to put my login ID into the dialout group.  Still no success.

Output from **inxi**:
```
ThinkPad-T430 log # inxi -Fxz
System:    Host: ThinkPad-T430 Kernel: 4.4.0-42-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: Cinnamon 3.0.7 (Gtk 3.18.9-1ubuntu3.1) Distro: Linux Mint 18 Sarah
Machine:   System: LENOVO (portable) product: 2349DG3 v: ThinkPad T430
           Mobo: LENOVO model: 2349DG3 Bios: LENOVO v: G1ETB0WW (2.70 ) date: 01/21/2016
CPU:       Dual core Intel Core i5-3380M (-HT-MCP-) cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 11573
           clock speeds: max: 3600 MHz 1: 1387 MHz 2: 1216 MHz 3: 1245 MHz 4: 1952 MHz
Graphics:  Card: Intel 3rd Gen Core processor Graphics Controller bus-ID: 00:02.0
           Display Server: X.org 1.18.3 drivers: intel (unloaded: fbdev,vesa)
           tty size: 238x32 Advanced Data: N/A for root
Audio:     Card Intel 7 Series/C210 Series Family High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.4.0-42-generic
Network:   Card-1: Intel 82579LM Gigabit Network Connection driver: e1000e v: 3.2.6-k port: 6080 bus-ID: 00:19.0
           IF: enp0s25 state: down mac: <filter>
           Card-2: Intel Centrino Advanced-N 6205 [Taylor Peak] driver: iwlwifi bus-ID: 03:00.0
           IF: wlp3s0 state: up mac: <filter>
Drives:    HDD Total Size: 128.0GB (56.8% used) ID-1: /dev/sda model: SAMSUNG_MZ7TD128 size: 128.0GB temp: 0C
Partition: ID-1: / size: 110G used: 61G (59%) fs: ext4 dev: /dev/dm-0
           ID-2: /boot size: 472M used: 256M (58%) fs: ext2 dev: /dev/sda1
           ID-3: swap-1 size: 8.27GB used: 0.00GB (0%) fs: swap dev: /dev/dm-1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 39.0C mobo: N/A
           Fan Speeds (in rpm): cpu: 2573
Info:      Processes: 219 Uptime: 24 min Memory: 1591.7/7685.0MB Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.421) inxi: 2.2.35 

```

Running **udevadm monitor** to see the USB activity,  I get the following if I plug in the Digispark Pro.  The device insert is registered and 5 seconds later it gets removed as the user program on the device kicks in:
```
ThinkPad-T430 log # udevadm monitor
monitor will print the received events for:
UDEV - the event which udev sends out after rule processing
KERNEL - the kernel uevent

KERNEL[226.971334] add      /devices/pci0000:00/0000:00:14.0/usb3/3-1 (usb)
KERNEL[226.972379] add      /devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0 (usb)
UDEV  [226.985551] add      /devices/pci0000:00/0000:00:14.0/usb3/3-1 (usb)
UDEV  [226.988657] add      /devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0 (usb)
KERNEL[230.697713] remove   /devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0 (usb)
KERNEL[230.697979] remove   /devices/pci0000:00/0000:00:14.0/usb3/3-1 (usb)
UDEV  [230.699870] remove   /devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0 (usb)
UDEV  [230.700689] remove   /devices/pci0000:00/0000:00:14.0/usb3/3-1 (usb)

```

For this same action, I get the following log entries from **dmesg**:
```
ThinkPad-T430 log # dmesg
[  226.770007] usb 3-1: new low-speed USB device number 2 using xhci_hcd
[  226.956840] usb 3-1: New USB device found, idVendor=16d0, idProduct=0753
[  226.956848] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[  227.015233] [UFW BLOCK] IN=wlp3s0 OUT= MAC= SRC=fe80:0000:0000:0000:7a0e:a432:d624:75ca DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=103344 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
[  227.015256] [UFW BLOCK] IN=wlp3s0 OUT= MAC= SRC=fe80:0000:0000:0000:7a0e:a432:d624:75ca DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=468828 PROTO=UDP SPT=8612 DPT=8610 LEN=24 
[  227.025522] [UFW BLOCK] IN=wlp3s0 OUT= MAC= SRC=fe80:0000:0000:0000:7a0e:a432:d624:75ca DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=103344 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
[  227.025553] [UFW BLOCK] IN=wlp3s0 OUT= MAC= SRC=fe80:0000:0000:0000:7a0e:a432:d624:75ca DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=468828 PROTO=UDP SPT=8612 DPT=8610 LEN=24 
[  230.683609] usb 3-1: USB disconnect, device number 2

```

I'm more of a Mac person so Linux is not my strong suite although I have previous Unix experience. Thanks for reading...

---

### Post by jeremy31 on 2016-10-20
Moved to Mint subforum

---

