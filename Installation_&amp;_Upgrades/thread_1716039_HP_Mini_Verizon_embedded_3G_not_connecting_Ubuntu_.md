---
title: "HP Mini Verizon embedded 3G not connecting Ubuntu 10.10"
date: 2011-03-27
forum: Installation &amp; Upgrades
---

### Post by miker101 on 2011-03-27
fresh install of ubuntu 10.10, cannot figure out how to connect the 3g after attempting to setup mobile broadband connection there are no options to connect as if the device is not found.

please help!

---

### Post by miker101 on 2011-03-27
HP Mini model: 110-3098NR
Qualcomm Gobi2000 3g modem

---

### Post by miker101 on 2011-03-28
So after digging I found my answers here:
[http://ubuntuforums.org/showthread.php?t=1456735&highlight=Qualcomm+Gobi2000](http://ubuntuforums.org/showthread.php?t=1456735&highlight=Qualcomm+Gobi2000)

---

### Post by rspinuz on 2011-03-28
[LEFT]I am having the same problem.

Also a fresh install

I found the following links:
[http://ubuntuforums.org/showthread.php?t=1456735&highlight=Qualcomm+Gobi2000](http://ubuntuforums.org/showthread.php?t=1456735&highlight=Qualcomm+Gobi2000)
[http://ubuntuforums.org/showthread.php?t=1630716&page=3](http://ubuntuforums.org/showthread.php?t=1630716&page=3)

I followed the instructions just like everyone else and could not get it to work 

Since I am running Ubuntu 10.10 with a 2.6.35 Kernel (installed and compiled by Ubuntu) there was no need to patch the kernel with qcserial.c because it is already compiled into it.

gobi-loader was installed via the repos, and is up to date.

Network Manager, and Modem Manager are also installed and up to date.

The network manager does pick up ttyUSB0, but shows nothing for Verizon, and manually adding the Verizon connection did not work either.

The following is the connection settings I used in the network manager after manually adding the connection:

Basic:
Phone Number: #777
Username "Verizon Phone number"@vzw3g.com
Password: vzw

Advanced:
APN: Left Balnk
Network ID: Left Blank
Type: Any
Pin: Left Blank


The following is some command outputs I thought might help with troubleshooting:

```

Linux remote-HP-Mini-1004 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux

```I only copied what I thought was relevant

```

root@remote-HP-Mini-1004:~# lshw
remote-hp-mini-1004       
    description: Notebook
    product: HP Mini 110-3000
    vendor: Hewlett-Packard
    version: 047E10000B202B00110300000
    serial: 5CH10600MS
    width: 32 bits
    capabilities: smbios-2.6 dmi-2.6
    configuration: boot=normal chassis=notebook uuid=FE1AD199-4266-68B0-21FF-68B599D42A1C
  *-core
       description: Motherboard
       product: 148A
       vendor: Hewlett-Packard
       physical id: 0
       version: 79.49
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.14 (11/12/2010)
          size: 1MiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb

``````

remote@remote-HP-Mini-1004:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04f2:b1eb Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 03f0:251d Hewlett-Packard Gobi 2000 Wireless Modem
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```The firmware is installed

```

remote@remote-HP-Mini-1004:~$ ls /lib/firmware/gobi
amss.mbn  apps.mbn  UQCN.mbn

```The device  ttyUSB0 is there

```

root@remote-HP-Mini-1004:~# ls -l /dev
total 0
crw-rw----  1 root video    10, 175 2011-03-28 19:11 agpgart
crw-------  1 root root     10, 235 2011-03-28 19:11 autofs
drwxr-xr-x  2 root root         600 2011-03-28 19:11 block
drwxr-xr-x  2 root root          60 2011-03-28 19:11 bsg
crw-------  1 root root     10, 234 2011-03-28 19:11 btrfs-control
drwxr-xr-x  3 root root          60 2011-03-28 19:11 bus
drwxr-xr-x  2 root root        3080 2011-03-28 19:11 char
crw-------  1 root root      5,   1 2011-03-28 19:11 console
lrwxrwxrwx  1 root root          11 2011-03-28 19:11 core -> /proc/kcore
drwxr-xr-x  2 root root          60 2011-03-28 19:11 cpu
crw-------  1 root root     10,  58 2011-03-28 19:11 cpu_dma_latency
drwxr-xr-x  5 root root         100 2011-03-28 19:11 disk
drwxr-xr-x  2 root root          80 2011-03-28 19:11 dri
crw-------  1 root root     10,  61 2011-03-28 19:11 ecryptfs
crw-rw----  1 root video    29,   0 2011-03-28 19:11 fb0
lrwxrwxrwx  1 root root          13 2011-03-28 19:11 fd -> /proc/self/fd
crw-rw-rw-  1 root root      1,   7 2011-03-28 19:11 full
crw-rw-rw-  1 root fuse     10, 229 2011-03-28 19:11 fuse
crw-------  1 root root     10, 228 2011-03-28 19:11 hpet
drwxr-xr-x  4 root root         320 2011-03-28 19:11 input
crw-------  1 root root      1,  11 2011-03-28 19:11 kmsg
srw-rw-rw-  1 root root           0 2011-03-28 19:11 log
brw-rw----  1 root disk      7,   0 2011-03-28 19:11 loop0
brw-rw----  1 root disk      7,   1 2011-03-28 19:11 loop1
brw-rw----  1 root disk      7,   2 2011-03-28 19:11 loop2
brw-rw----  1 root disk      7,   3 2011-03-28 19:11 loop3
brw-rw----  1 root disk      7,   4 2011-03-28 19:11 loop4
brw-rw----  1 root disk      7,   5 2011-03-28 19:11 loop5
brw-rw----  1 root disk      7,   6 2011-03-28 19:11 loop6
brw-rw----  1 root disk      7,   7 2011-03-28 19:11 loop7
drwxr-xr-x  2 root root          60 2011-03-28 19:11 mapper
crw-------  1 root root     10, 227 2011-03-28 19:11 mcelog
crw-r-----  1 root kmem      1,   1 2011-03-28 19:11 mem
drwxr-xr-x  2 root root          60 2010-10-07 08:58 net
crw-------  1 root root     10,  57 2011-03-28 19:11 network_latency
crw-------  1 root root     10,  56 2011-03-28 19:11 network_throughput
crw-rw-rw-  1 root root      1,   3 2011-03-28 19:11 null
crw-------  1 root root      1,  12 2011-03-28 19:11 oldmem
drwxr-xr-x  2 root root          60 2011-03-28 19:11 pktcdvd
crw-r-----  1 root kmem      1,   4 2011-03-28 19:11 port
crw-------  1 root root    108,   0 2011-03-28 19:11 ppp
crw-------  1 root root     10,   1 2011-03-28 19:11 psaux
crw-rw-rw-  1 root tty       5,   2 2011-03-28 20:11 ptmx
drwxr-xr-x  2 root root           0 2010-09-24 05:25 pts
brw-rw----  1 root disk      1,   0 2011-03-28 19:11 ram0
brw-rw----  1 root disk      1,   1 2011-03-28 19:11 ram1
brw-rw----  1 root disk      1,  10 2011-03-28 19:11 ram10
brw-rw----  1 root disk      1,  11 2011-03-28 19:11 ram11
brw-rw----  1 root disk      1,  12 2011-03-28 19:11 ram12
brw-rw----  1 root disk      1,  13 2011-03-28 19:11 ram13
brw-rw----  1 root disk      1,  14 2011-03-28 19:11 ram14
brw-rw----  1 root disk      1,  15 2011-03-28 19:11 ram15
brw-rw----  1 root disk      1,   2 2011-03-28 19:11 ram2
brw-rw----  1 root disk      1,   3 2011-03-28 19:11 ram3
brw-rw----  1 root disk      1,   4 2011-03-28 19:11 ram4
brw-rw----  1 root disk      1,   5 2011-03-28 19:11 ram5
brw-rw----  1 root disk      1,   6 2011-03-28 19:11 ram6
brw-rw----  1 root disk      1,   7 2011-03-28 19:11 ram7
brw-rw----  1 root disk      1,   8 2011-03-28 19:11 ram8
brw-rw----  1 root disk      1,   9 2011-03-28 19:11 ram9
crw-rw-rw-  1 root root      1,   8 2011-03-28 19:11 random
crw-rw-r--+ 1 root root     10,  62 2011-03-28 19:11 rfkill
lrwxrwxrwx  1 root root           4 2011-03-28 19:11 root -> sda1
lrwxrwxrwx  1 root root           4 2011-03-28 19:11 rtc -> rtc0
crw-------  1 root root    254,   0 2011-03-28 19:11 rtc0
brw-rw----  1 root disk      8,   0 2011-03-28 19:11 sda
brw-rw----  1 root disk      8,   1 2011-03-28 19:11 sda1
brw-rw----  1 root disk      8,   2 2011-03-28 19:11 sda2
brw-rw----  1 root disk      8,   5 2011-03-28 19:11 sda5
drwxr-xr-x  4 root root          80 2011-03-28 19:11 serial
crw-rw----  1 root disk     21,   0 2011-03-28 19:11 sg0
drwxrwxrwt  2 root root         120 2011-03-28 19:34 shm
crw-------  1 root root     10, 231 2011-03-28 19:11 snapshot
drwxr-xr-x  3 root root         180 2011-03-28 19:11 snd
lrwxrwxrwx  1 root root          15 2011-03-28 19:11 stderr -> /proc/self/fd/2
lrwxrwxrwx  1 root root          15 2011-03-28 19:11 stdin -> /proc/self/fd/0
lrwxrwxrwx  1 root root          15 2011-03-28 19:11 stdout -> /proc/self/fd/1
crw-rw-rw-  1 root tty       5,   0 2011-03-28 19:11 tty
crw--w----  1 root root      4,   0 2011-03-28 19:11 tty0
crw-------  1 root root      4,   1 2011-03-28 19:11 tty1
crw--w----  1 root tty       4,  10 2011-03-28 19:11 tty10
crw--w----  1 root tty       4,  11 2011-03-28 19:11 tty11
crw--w----  1 root tty       4,  12 2011-03-28 19:11 tty12
crw--w----  1 root tty       4,  13 2011-03-28 19:11 tty13
crw--w----  1 root tty       4,  14 2011-03-28 19:11 tty14
crw--w----  1 root tty       4,  15 2011-03-28 19:11 tty15
crw--w----  1 root tty       4,  16 2011-03-28 19:11 tty16
crw--w----  1 root tty       4,  17 2011-03-28 19:11 tty17
crw--w----  1 root tty       4,  18 2011-03-28 19:11 tty18
crw--w----  1 root tty       4,  19 2011-03-28 19:11 tty19
crw-------  1 root root      4,   2 2011-03-28 19:11 tty2
crw--w----  1 root tty       4,  20 2011-03-28 19:11 tty20
crw--w----  1 root tty       4,  21 2011-03-28 19:11 tty21
crw--w----  1 root tty       4,  22 2011-03-28 19:11 tty22
crw--w----  1 root tty       4,  23 2011-03-28 19:11 tty23
crw--w----  1 root tty       4,  24 2011-03-28 19:11 tty24
crw--w----  1 root tty       4,  25 2011-03-28 19:11 tty25
crw--w----  1 root tty       4,  26 2011-03-28 19:11 tty26
crw--w----  1 root tty       4,  27 2011-03-28 19:11 tty27
crw--w----  1 root tty       4,  28 2011-03-28 19:11 tty28
crw--w----  1 root tty       4,  29 2011-03-28 19:11 tty29
crw-------  1 root root      4,   3 2011-03-28 19:11 tty3
crw--w----  1 root tty       4,  30 2011-03-28 19:11 tty30
crw--w----  1 root tty       4,  31 2011-03-28 19:11 tty31
crw--w----  1 root tty       4,  32 2011-03-28 19:11 tty32
crw--w----  1 root tty       4,  33 2011-03-28 19:11 tty33
crw--w----  1 root tty       4,  34 2011-03-28 19:11 tty34
crw--w----  1 root tty       4,  35 2011-03-28 19:11 tty35
crw--w----  1 root tty       4,  36 2011-03-28 19:11 tty36
crw--w----  1 root tty       4,  37 2011-03-28 19:11 tty37
crw--w----  1 root tty       4,  38 2011-03-28 19:11 tty38
crw--w----  1 root tty       4,  39 2011-03-28 19:11 tty39
crw-------  1 root root      4,   4 2011-03-28 19:11 tty4
crw--w----  1 root tty       4,  40 2011-03-28 19:11 tty40
crw--w----  1 root tty       4,  41 2011-03-28 19:11 tty41
crw--w----  1 root tty       4,  42 2011-03-28 19:11 tty42
crw--w----  1 root tty       4,  43 2011-03-28 19:11 tty43
crw--w----  1 root tty       4,  44 2011-03-28 19:11 tty44
crw--w----  1 root tty       4,  45 2011-03-28 19:11 tty45
crw--w----  1 root tty       4,  46 2011-03-28 19:11 tty46
crw--w----  1 root tty       4,  47 2011-03-28 19:11 tty47
crw--w----  1 root tty       4,  48 2011-03-28 19:11 tty48
crw--w----  1 root tty       4,  49 2011-03-28 19:11 tty49
crw-------  1 root root      4,   5 2011-03-28 19:11 tty5
crw--w----  1 root tty       4,  50 2011-03-28 19:11 tty50
crw--w----  1 root tty       4,  51 2011-03-28 19:11 tty51
crw--w----  1 root tty       4,  52 2011-03-28 19:11 tty52
crw--w----  1 root tty       4,  53 2011-03-28 19:11 tty53
crw--w----  1 root tty       4,  54 2011-03-28 19:11 tty54
crw--w----  1 root tty       4,  55 2011-03-28 19:11 tty55
crw--w----  1 root tty       4,  56 2011-03-28 19:11 tty56
crw--w----  1 root tty       4,  57 2011-03-28 19:11 tty57
crw--w----  1 root tty       4,  58 2011-03-28 19:11 tty58
crw--w----  1 root tty       4,  59 2011-03-28 19:11 tty59
crw-------  1 root root      4,   6 2011-03-28 19:11 tty6
crw--w----  1 root tty       4,  60 2011-03-28 19:11 tty60
crw--w----  1 root tty       4,  61 2011-03-28 19:11 tty61
crw--w----  1 root tty       4,  62 2011-03-28 19:11 tty62
crw--w----  1 root tty       4,  63 2011-03-28 19:11 tty63
crw--w----  1 root root      4,   7 2011-03-28 19:11 tty7
crw--w----  1 root tty       4,   8 2011-03-28 19:11 tty8
crw--w----  1 root tty       4,   9 2011-03-28 19:11 tty9
crw-rw----  1 root dialout   4,  64 2011-03-28 19:11 ttyS0
crw-rw----  1 root dialout   4,  65 2011-03-28 19:11 ttyS1
crw-rw----  1 root dialout   4,  66 2011-03-28 19:11 ttyS2
crw-rw----  1 root dialout   4,  67 2011-03-28 19:11 ttyS3
crw-rw----  1 root dialout 188,   0 2011-03-28 20:11 ttyUSB0
crw-r-----  1 root root     10, 223 2011-03-28 19:11 uinput
crw-rw-rw-  1 root root      1,   9 2011-03-28 19:11 urandom
crw-------  1 root root    252,   0 2011-03-28 19:11 usbmon0
crw-------  1 root root    252,   1 2011-03-28 19:11 usbmon1
crw-------  1 root root    252,   2 2011-03-28 19:11 usbmon2
crw-------  1 root root    252,   3 2011-03-28 19:11 usbmon3
crw-------  1 root root    252,   4 2011-03-28 19:11 usbmon4
crw-------  1 root root    252,   5 2011-03-28 19:11 usbmon5
drwxr-xr-x  4 root root          80 2011-03-28 19:11 v4l
crw-rw----  1 root tty       7,   0 2011-03-28 19:11 vcs
crw-rw----  1 root tty       7,   1 2011-03-28 19:11 vcs1
crw-rw----  1 root tty       7,   2 2011-03-28 19:11 vcs2
crw-rw----  1 root tty       7,   3 2011-03-28 19:11 vcs3
crw-rw----  1 root tty       7,   4 2011-03-28 19:11 vcs4
crw-rw----  1 root tty       7,   5 2011-03-28 19:11 vcs5
crw-rw----  1 root tty       7,   6 2011-03-28 19:11 vcs6
crw-rw----  1 root tty       7,   7 2011-03-28 19:11 vcs7
crw-rw----  1 root tty       7, 128 2011-03-28 19:11 vcsa
crw-rw----  1 root tty       7, 129 2011-03-28 19:11 vcsa1
crw-rw----  1 root tty       7, 130 2011-03-28 19:11 vcsa2
crw-rw----  1 root tty       7, 131 2011-03-28 19:11 vcsa3
crw-rw----  1 root tty       7, 132 2011-03-28 19:11 vcsa4
crw-rw----  1 root tty       7, 133 2011-03-28 19:11 vcsa5
crw-rw----  1 root tty       7, 134 2011-03-28 19:11 vcsa6
crw-rw----  1 root tty       7, 135 2011-03-28 19:11 vcsa7
crw-------  1 root root     10,  63 2011-03-28 19:11 vga_arbiter
crw-rw----+ 1 root video    81,   0 2011-03-28 19:11 video0
crw-rw-rw-  1 root root      1,   5 2011-03-28 19:11 zero

``````

root@remote-HP-Mini-1004:~# dmesg | grep -i qcs
[   14.444199] qcserial 1-6:1.2: Qualcomm USB modem converter detected
[   14.449272] usbcore: registered new interface driver qcserial

``````

root@remote-HP-Mini-1004:~# dmesg | grep -e "modem" -e "tty"
[    0.000000] console [tty0] enabled
[   14.435490] USB Serial support registered for Qualcomm USB modem
[   14.444199] qcserial 1-6:1.2: Qualcomm USB modem converter detected
[   14.448791] usb 1-6: Qualcomm USB modem converter now attached to ttyUSB0

``````

root@remote-HP-Mini-1004:/lib/udev/rules.d# cat 60-gobi.rules
# udev rules for firmware loading on qualcomm gobi devices

ACTION=="add", SUBSYSTEM=="tty", KERNEL=="ttyUSB*", GOTO="gobi_rules"

GOTO="gobi_rules_end"

LABEL="gobi_rules"
ATTRS{idVendor}=="05c6", ATTRS{idProduct}=="9211", RUN+="gobi_loader $env{DEVNAME} /lib/firmware/gobi"
ATTRS{idVendor}=="03f0", ATTRS{idProduct}=="201d", RUN+="gobi_loader $env{DEVNAME} /lib/firmware/gobi"
ATTRS{idVendor}=="04da", ATTRS{idProduct}=="250c", RUN+="gobi_loader $env{DEVNAME} /lib/firmware/gobi"
ATTRS{idVendor}=="413c", ATTRS{idProduct}=="8171", RUN+="gobi_loader $env{DEVNAME} /lib/firmware/gobi"
ATTRS{idVendor}=="1410", ATTRS{idProduct}=="a008", RUN+="gobi_loader $env{DEVNAME} /lib/firmware/gobi"
ATTRS{idVendor}=="0b05", ATTRS{idProduct}=="1774", RUN+="gobi_loader $env{DEVNAME} /lib/firmware/gobi"
ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="fff2", RUN+="gobi_loader $env{DEVNAME} /lib/firmware/gobi"
ATTRS{idVendor}=="1557", ATTRS{idProduct}=="0a80", RUN+="gobi_loader $env{DEVNAME} /lib/firmware/gobi"
ATTRS{idVendor}=="05c6", ATTRS{idProduct}=="9008", RUN+="gobi_loader $env{DEVNAME} /lib/firmware/gobi"
ATTRS{idVendor}=="05c6", ATTRS{idProduct}=="9201", RUN+="gobi_loader $env{DEVNAME} /lib/firmware/gobi"
ATTRS{idVendor}=="05c6", ATTRS{idProduct}=="9221", RUN+="gobi_loader $env{DEVNAME} /lib/firmware/gobi"
ATTRS{idVendor}=="05c6", ATTRS{idProduct}=="9231", RUN+="gobi_loader $env{DEVNAME} /lib/firmware/gobi"
ATTRS{idVendor}=="1f45", ATTRS{idProduct}=="0001", RUN+="gobi_loader $env{DEVNAME} /lib/firmware/gobi"
ATTRS{idVendor}=="16d8", ATTRS{idProduct}=="8001", RUN+="gobi_loader -2000 $env{DEVNAME} /lib/firmware/gobi"
ATTRS{idVendor}=="1199", ATTRS{idProduct}=="9000", RUN+="gobi_loader -2000 $env{DEVNAME} /lib/firmware/gobi"
ATTRS{idVendor}=="03f0", ATTRS{idProduct}=="241d", RUN+="gobi_loader -2000 $env{DEVNAME} /lib/firmware/gobi"
ATTRS{idVendor}=="05c6", ATTRS{idProduct}=="9204", RUN+="gobi_loader -2000 $env{DEVNAME} /lib/firmware/gobi"
ATTRS{idVendor}=="05c6", ATTRS{idProduct}=="9214", RUN+="gobi_loader -2000 $env{DEVNAME} /lib/firmware/gobi"
ATTRS{idVendor}=="05c6", ATTRS{idProduct}=="9224", RUN+="gobi_loader -2000 $env{DEVNAME} /lib/firmware/gobi"
ATTRS{idVendor}=="05c6", ATTRS{idProduct}=="9234", RUN+="gobi_loader -2000 $env{DEVNAME} /lib/firmware/gobi"
ATTRS{idVendor}=="05c6", ATTRS{idProduct}=="9244", RUN+="gobi_loader -2000 $env{DEVNAME} /lib/firmware/gobi"
ATTRS{idVendor}=="05c6", ATTRS{idProduct}=="9264", RUN+="gobi_loader -2000 $env{DEVNAME} /lib/firmware/gobi"
ATTRS{idVendor}=="05c6", ATTRS{idProduct}=="9274", RUN+="gobi_loader -2000 $env{DEVNAME} /lib/firmware/gobi"
ATTRS{idVendor}=="413c", ATTRS{idProduct}=="8185", RUN+="gobi_loader -2000 $env{DEVNAME} /lib/firmware/gobi"

LABEL="gobi_rules_end"

``````

root@remote-HP-Mini-1004:/lib/udev/rules.d# cat 77-mm-usb-device-blacklist.rules
# do not edit this file, it will be overwritten on update

ACTION!="add|change", GOTO="mm_usb_device_blacklist_end"
SUBSYSTEM!="usb", GOTO="mm_usb_device_blacklist_end"
ENV{DEVTYPE}!="usb_device",  GOTO="mm_usb_device_blacklist_end"

# APC UPS devices
ATTRS{idVendor}=="051d", ENV{ID_MM_DEVICE_IGNORE}="1"

# Sweex 1000VA
ATTRS{idVendor}=="0925", ATTRS{idProduct}=="1234", ENV{ID_MM_DEVICE_IGNORE}="1"

# Agiler UPS
ATTRS{idVendor}=="05b8", ATTRS{idProduct}=="0000", ENV{ID_MM_DEVICE_IGNORE}="1"

# Krauler UP-M500VA
ATTRS{idVendor}=="0001", ATTRS{idProduct}=="0000", ENV{ID_MM_DEVICE_IGNORE}="1"

# Ablerex 625L USB
ATTRS{idVendor}=="ffff", ATTRS{idProduct}=="0000", ENV{ID_MM_DEVICE_IGNORE}="1"

# Belkin F6C1200-UNV
ATTRS{idVendor}=="0665", ATTRS{idProduct}=="5161", ENV{ID_MM_DEVICE_IGNORE}="1"

# Various Liebert and Phoenixtec Power devices
ATTRS{idVendor}=="06da", ENV{ID_MM_DEVICE_IGNORE}="1"

# Unitek Alpha 1200Sx
ATTRS{idVendor}=="0f03", ATTRS{idProduct}=="0001", ENV{ID_MM_DEVICE_IGNORE}="1"

# Various Tripplite devices
ATTRS{idVendor}=="09ae", ENV{ID_MM_DEVICE_IGNORE}="1"

# Various MGE Office Protection Systems devices
ATTRS{idVendor}=="0463", ATTRS{idProduct}=="0001", ENV{ID_MM_DEVICE_IGNORE}="1"
ATTRS{idVendor}=="0463", ATTRS{idProduct}=="ffff", ENV{ID_MM_DEVICE_IGNORE}="1"

# CyberPower 900AVR/BC900D
ATTRS{idVendor}=="0764", ATTRS{idProduct}=="0005", ENV{ID_MM_DEVICE_IGNORE}="1"
# CyberPower CP1200AVR/BC1200D
ATTRS{idVendor}=="0764", ATTRS{idProduct}=="0501", ENV{ID_MM_DEVICE_IGNORE}="1"

# Various Belkin devices
ATTRS{idVendor}=="050d", ATTRS{idProduct}=="0980", ENV{ID_MM_DEVICE_IGNORE}="1"
ATTRS{idVendor}=="050d", ATTRS{idProduct}=="0900", ENV{ID_MM_DEVICE_IGNORE}="1"
ATTRS{idVendor}=="050d", ATTRS{idProduct}=="0910", ENV{ID_MM_DEVICE_IGNORE}="1"
ATTRS{idVendor}=="050d", ATTRS{idProduct}=="0912", ENV{ID_MM_DEVICE_IGNORE}="1"
ATTRS{idVendor}=="050d", ATTRS{idProduct}=="0551", ENV{ID_MM_DEVICE_IGNORE}="1"
ATTRS{idVendor}=="050d", ATTRS{idProduct}=="0751", ENV{ID_MM_DEVICE_IGNORE}="1"
ATTRS{idVendor}=="050d", ATTRS{idProduct}=="0375", ENV{ID_MM_DEVICE_IGNORE}="1"
ATTRS{idVendor}=="050d", ATTRS{idProduct}=="1100", ENV{ID_MM_DEVICE_IGNORE}="1"

# HP R/T 2200 INTL (like SMART2200RMXL2U)
ATTRS{idVendor}=="03f0", ATTRS{idProduct}=="1f0a", ENV{ID_MM_DEVICE_IGNORE}="1"

# Powerware devices
ATTRS{idVendor}=="0592", ATTRS{idProduct}=="0002", ENV{ID_MM_DEVICE_IGNORE}="1"

# Palm Treo 700/900/etc
# Shouldn't be probed themselves, but you can install programs like
# "MobileStream USB Modem" which changes the USB PID of the device to something
# that isn't blacklisted.
ATTRS{idVendor}=="0830", ATTRS{idProduct}=="0061", ENV{ID_MM_DEVICE_IGNORE}="1"

# Qualcomm Gobi 2000 QDL
ATTRS{idVendor}=="03f0", ATTRS{idProduct}=="241d", ENV{ID_MM_DEVICE_IGNORE}="1"

LABEL="mm_usb_device_blacklist_end"

``````

root@remote-HP-Mini-1004:~# cat /var/log/daemon.log | grep NetworkManager
Mar 28 19:15:27 remote-HP-Mini-1004 NetworkManager[804]: <info> Activation (ttyUSB0) starting connection 'Verizon connection'
Mar 28 19:15:27 remote-HP-Mini-1004 NetworkManager[804]: <info> (ttyUSB0): device state change: 3 -> 4 (reason 0)
Mar 28 19:15:27 remote-HP-Mini-1004 NetworkManager[804]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 28 19:15:27 remote-HP-Mini-1004 NetworkManager[804]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...
Mar 28 19:15:27 remote-HP-Mini-1004 NetworkManager[804]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.
Mar 28 19:16:28 remote-HP-Mini-1004 NetworkManager[804]: <warn> GSM connection failed: (32) Network timeout
Mar 28 19:16:28 remote-HP-Mini-1004 NetworkManager[804]: <info> (ttyUSB0): device state change: 4 -> 9 (reason 1)
Mar 28 19:16:28 remote-HP-Mini-1004 NetworkManager[804]: <info> Marking connection 'Verizon connection' invalid.
Mar 28 19:16:28 remote-HP-Mini-1004 NetworkManager[804]: <warn> Activation (ttyUSB0) failed.
Mar 28 19:16:28 remote-HP-Mini-1004 NetworkManager[804]: <info> (ttyUSB0): device state change: 9 -> 3 (reason 0)
Mar 28 19:16:28 remote-HP-Mini-1004 NetworkManager[804]: <info> (ttyUSB0): deactivating device (reason: 0).

```Like I said everything is installed and seams to work with the exception of not being able to connect to Verizons 3g network.  Why I do not have the slighest clue.

I do know that the 3g worked, and connected when Windows 7 Starter edition was installed.

I hate Windows more then you will ever know, and reverting back to it is not an option.

If there is anyone who has any insight on this problem, or can shead some light on it so tha I may continue to use a free and open OS I Thank You in advance.

If there is any other information that I can provide you with please  let me know.

Thank You,

Ryan
[/LEFT]

---

