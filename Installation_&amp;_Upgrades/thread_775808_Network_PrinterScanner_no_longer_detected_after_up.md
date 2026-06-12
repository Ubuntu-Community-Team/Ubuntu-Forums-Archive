---
title: "Network Printer/Scanner no longer detected after upgrade to Hardy 8.04"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by jpeach on 2008-04-30
Hello:

My networked Brother MFC-5440CN was working great (scanner and printer) under Ubuntu 7.10 on my Thinkpad T30 (x86) and T61 (amd64).  The printer/scanner is connected via the network on a static IP  (not a USB connection).  When I upgraded to Ubuntu 8.04 it broke the scanning and printing functions.  

When xsane runs it is not able to detect the scanner.  The following entry is posted to the syslog:

```
Apr 30 09:52:23 leda kernel: [ 3331.495670] ppdev0: registered pardevice
Apr 30 09:52:23 leda kernel: [ 3331.496139] ppdev0: unregistered pardevice
Apr 30 09:52:24 leda kernel: [ 2219.999012] ppdev0: registered pardevice
Apr 30 09:52:24 leda xsane: io/hpmud/pp.c 627: unable to read device-id ret=-1 
Apr 30 09:52:24 leda kernel: [ 2220.046857] ppdev0: unregistered pardevice

```

"brsaneconfig2 -q" shows that the printer is configured as:
```
Devices on network
  0 juliet     "MFC-5440CN"     N:BRN_JULIET

```

This is the results of "brsaneconfig2 -d":
```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/mapper/leda-root
UUID=ab736edc-10a9-4b5d-abc7-4948f91e010f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=b3573288-6c97-4715-afd7-9a17ba9d52e9 /boot           ext3    defaults        0       2
# /dev/mapper/leda-swap_1
UUID=6e8f67a4-3dcb-46a2-87ac-dffcb114a713 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
-----------------------------
sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
-----------------------------
ls -R -all /proc/bus/usb
/proc/bus/usb:
total 0
dr-xr-xr-x 2 root root 0 2008-04-30 10:01 .
dr-xr-xr-x 6 root root 0 2008-04-30 00:52 ..
-----------------------------
cat /proc/bus/usb/devices
cat: /proc/bus/usb/devices: No such file or directory
-----------------------------
scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
-----------------------------
-----------------------------
/usr/local/Brother/sane/brsanenetdevice2.cfg:
DEVICE=juliet , "MFC-5440CN" , 0x4f9:0x16d , NODENAME=BRN_JULIET 

-----------------------------
/usr/local/Brother/sane/Brsane2.ini:
[Support Model]
0x0161,10,1,"MFC-210C"
0x0162,12,1,"MFC-420CN"
0x0163,10,1,"MFC-410CN"
0x0165,12,1,"MFC-620CN"
0x0166,10,1,"MFC-610CLN"
0x0168,10,1,"MFC-620CLN"
0x0169,10,2,"DCP-110C"
0x016b,10,2,"DCP-310CN"
0x016d,12,1,"MFC-5440CN"
0x016e,12,1,"MFC-5840CN"
0x0173,11,1,"MFC-3240C"
0x0174,11,1,"MFC-3340CN"

0x0180, 6,1,"MFC-7420"
0x0181, 6,1,"MFC-7820N"
0x0182, 7,2,"DCP-7010"
0x0183, 6,2,"DCP-7020"
0x0184, 6,2,"DCP-7025"
0x0185, 5,1,"MFC-7220"
0x0186, 5,1,"MFC-7225N"

0x018a, 16,1,"MFC-9420CN"

0x1a3,  8,2, "DCP-8060"
0x1a4,108,2, "DCP-8065DN"
0x1a5,  8,1, "MFC-8460N"
0x1a6,108,1, "MFC-8860DN"
0x1a7,108,1, "MFC-8870DW"
0x1bd,  8,1, "MFC-8660DN"

0x018c,10,2,"DCP-115C"
0x018d,10,2,"DCP-116C"
0x018e,10,2,"DCP-117C"
0x018f,10,2,"DCP-118C"
0x0190,12,2,"DCP-120C"
0x0191,10,2,"DCP-315CN"
0x0192,12,2,"DCP-340CW"
0x0193,10,1,"MFC-215C"
0x0194,12,1,"MFC-425CN"
0x0195,12,1,"MFC-820CW"
0x0196,12,1,"MFC-820CN"
0x0197,12,1,"MFC-640CW"
0x0198,10,1,"MFC-615CL"
0x0199,10,1,"MFC-830CLN"
0x019a,12,1,"MFC-840CLN"

0x01a8,10,2,"DCP-130C"
0x01a9,10,2,"DCP-330C"
0x01aa,12,2,"DCP-540CN"
0x01ab,12,1,"MFC-240C"
0x01ae,10,2,"DCP-750CW"
0x01af,12,1,"MFC-440CN"
0x01b0,12,1,"MFC-660CN"
0x01b1,12,1,"MFC-665CW"
0x01b2,12,1,"MFC-845CW"
0x01b4,12,1,"MFC-460CN"
0x01b5,10,1,"MFC-630CD"
0x01b6,10,1,"MFC-850CDN"
0x01b7,12,1,"MFC-5460CN"
0x01b8,12,1,"MFC-5860CN"
0x01ba,11,1,"MFC-3360C"
0x01be,10,2,"DCP-750CN"
0x01bf,12,1,"MFC-860CDN"

[ModelTypeName]
1=MFC Scanner
2=DCP Scanner

[Driver]
scanfast24=0
NoUseCM=0
compression=1
Inqueue=32000
LogFile=0

-----------------------------
/usr/local/Brother/sane/models2/ext1.ini:
[Support Model]
0x01c9,  16,2,"DCP-9040CN"
0x01ca,  16,1,"MFC-9440CN"
0x01cb, 116,2,"DCP-9045CDN"
0x01cc, 116,1,"MFC-9840CDW"
0x01ec, 116,1,"MFC-9640CW"



0x01e4, 10,2,"DCP-357C"
0x01e3, 10,2,"DCP-353C"
0x01e2, 10,2,"DCP-157C"
0x01e1, 10,2,"DCP-153C"
0x01e0, 12,1,"MFC-265C"
0x01df, 10,2,"DCP-155C"
0x01de, 12,1,"MFC-880CDN"
0x01dd, 10,1,"MFC-870CDN"
0x01dc, 10,1,"MFC-650CD"
0x01db, 12,1,"MFC-480CN"
0x01da, 12,1,"MFC-885CW"
0x01d9, 12,1,"MFC-685CW"
0x01d8, 12,1,"MFC-680CN"
0x01d7, 12,1,"MFC-465CN"
0x01d6, 12,1,"MFC-260C"
0x01d5, 10,1,"MFC-235C"
0x01d4, 10,1,"MFC-230C"
0x01d3, 10,2,"DCP-770CN"
0x01d2, 10,2,"DCP-770CW"
0x01d1, 12,2,"DCP-560CN"
0x01d0, 10,2,"DCP-350C"
0x01cf, 10,2,"DCP-150C"
0x01ce, 10,2,"DCP-135C"

-----------------------------
MODEL:"DCP-9040CN",ID:0x4f9:0x1c9,TYPE:16,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-9440CN",ID:0x4f9:0x1ca,TYPE:16,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-9045CDN",ID:0x4f9:0x1cb,TYPE:16,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-9840CDW",ID:0x4f9:0x1cc,TYPE:16,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-9640CW",ID:0x4f9:0x1ec,TYPE:16,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-357C",ID:0x4f9:0x1e4,TYPE:10,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-353C",ID:0x4f9:0x1e3,TYPE:10,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-157C",ID:0x4f9:0x1e2,TYPE:10,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-153C",ID:0x4f9:0x1e1,TYPE:10,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-265C",ID:0x4f9:0x1e0,TYPE:12,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-155C",ID:0x4f9:0x1df,TYPE:10,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-880CDN",ID:0x4f9:0x1de,TYPE:12,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-870CDN",ID:0x4f9:0x1dd,TYPE:10,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-650CD",ID:0x4f9:0x1dc,TYPE:10,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-480CN",ID:0x4f9:0x1db,TYPE:12,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-885CW",ID:0x4f9:0x1da,TYPE:12,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-685CW",ID:0x4f9:0x1d9,TYPE:12,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-680CN",ID:0x4f9:0x1d8,TYPE:12,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-465CN",ID:0x4f9:0x1d7,TYPE:12,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-260C",ID:0x4f9:0x1d6,TYPE:12,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-235C",ID:0x4f9:0x1d5,TYPE:10,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-230C",ID:0x4f9:0x1d4,TYPE:10,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-770CN",ID:0x4f9:0x1d3,TYPE:10,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-770CW",ID:0x4f9:0x1d2,TYPE:10,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-560CN",ID:0x4f9:0x1d1,TYPE:12,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-350C",ID:0x4f9:0x1d0,TYPE:10,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-150C",ID:0x4f9:0x1cf,TYPE:10,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-135C",ID:0x4f9:0x1ce,TYPE:10,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-210C",ID:0x4f9:0x161,TYPE:10,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-420CN",ID:0x4f9:0x162,TYPE:12,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-410CN",ID:0x4f9:0x163,TYPE:10,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-620CN",ID:0x4f9:0x165,TYPE:12,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-610CLN",ID:0x4f9:0x166,TYPE:10,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-620CLN",ID:0x4f9:0x168,TYPE:10,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-110C",ID:0x4f9:0x169,TYPE:10,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-310CN",ID:0x4f9:0x16b,TYPE:10,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-5440CN",ID:0x4f9:0x16d,TYPE:12,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-5840CN",ID:0x4f9:0x16e,TYPE:12,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-3240C",ID:0x4f9:0x173,TYPE:11,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-3340CN",ID:0x4f9:0x174,TYPE:11,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-7420",ID:0x4f9:0x180,TYPE:6,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-7820N",ID:0x4f9:0x181,TYPE:6,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-7010",ID:0x4f9:0x182,TYPE:7,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-7020",ID:0x4f9:0x183,TYPE:6,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-7025",ID:0x4f9:0x184,TYPE:6,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-7220",ID:0x4f9:0x185,TYPE:5,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-7225N",ID:0x4f9:0x186,TYPE:5,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-9420CN",ID:0x4f9:0x18a,TYPE:16,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-8060",ID:0x4f9:0x1a3,TYPE:8,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-8065DN",ID:0x4f9:0x1a4,TYPE:8,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-8460N",ID:0x4f9:0x1a5,TYPE:8,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-8860DN",ID:0x4f9:0x1a6,TYPE:8,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-8870DW",ID:0x4f9:0x1a7,TYPE:8,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-8660DN",ID:0x4f9:0x1bd,TYPE:8,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-115C",ID:0x4f9:0x18c,TYPE:10,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-116C",ID:0x4f9:0x18d,TYPE:10,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-117C",ID:0x4f9:0x18e,TYPE:10,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-118C",ID:0x4f9:0x18f,TYPE:10,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-120C",ID:0x4f9:0x190,TYPE:12,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-315CN",ID:0x4f9:0x191,TYPE:10,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-340CW",ID:0x4f9:0x192,TYPE:12,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-215C",ID:0x4f9:0x193,TYPE:10,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-425CN",ID:0x4f9:0x194,TYPE:12,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-820CW",ID:0x4f9:0x195,TYPE:12,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-820CN",ID:0x4f9:0x196,TYPE:12,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-640CW",ID:0x4f9:0x197,TYPE:12,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-615CL",ID:0x4f9:0x198,TYPE:10,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-830CLN",ID:0x4f9:0x199,TYPE:10,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-840CLN",ID:0x4f9:0x19a,TYPE:12,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-130C",ID:0x4f9:0x1a8,TYPE:10,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-330C",ID:0x4f9:0x1a9,TYPE:10,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-540CN",ID:0x4f9:0x1aa,TYPE:12,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-240C",ID:0x4f9:0x1ab,TYPE:12,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-750CW",ID:0x4f9:0x1ae,TYPE:10,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-440CN",ID:0x4f9:0x1af,TYPE:12,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-660CN",ID:0x4f9:0x1b0,TYPE:12,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-665CW",ID:0x4f9:0x1b1,TYPE:12,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-845CW",ID:0x4f9:0x1b2,TYPE:12,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-460CN",ID:0x4f9:0x1b4,TYPE:12,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-630CD",ID:0x4f9:0x1b5,TYPE:10,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-850CDN",ID:0x4f9:0x1b6,TYPE:10,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-5460CN",ID:0x4f9:0x1b7,TYPE:12,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-5860CN",ID:0x4f9:0x1b8,TYPE:12,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-3360C",ID:0x4f9:0x1ba,TYPE:11,1,RE:0xffff,WE:0xffff CM:,,
MODEL:"DCP-750CN",ID:0x4f9:0x1be,TYPE:10,2,RE:0xffff,WE:0xffff CM:,,
MODEL:"MFC-860CDN",ID:0x4f9:0x1bf,TYPE:12,1,RE:0xffff,WE:0xffff CM:,,
-----------------------------
  0 "DCP-9040CN"
  1 "MFC-9440CN"
  2 "DCP-9045CDN"
  3 "MFC-9840CDW"
  4 "MFC-9640CW"
  5 "DCP-357C"
  6 "DCP-353C"
  7 "DCP-157C"
  8 "DCP-153C"
  9 "MFC-265C"
 10 "DCP-155C"
 11 "MFC-880CDN"
 12 "MFC-870CDN"
 13 "MFC-650CD"
 14 "MFC-480CN"
 15 "MFC-885CW"
 16 "MFC-685CW"
 17 "MFC-680CN"
 18 "MFC-465CN"
 19 "MFC-260C"
 20 "MFC-235C"
 21 "MFC-230C"
 22 "DCP-770CN"
 23 "DCP-770CW"
 24 "DCP-560CN"
 25 "DCP-350C"
 26 "DCP-150C"
 27 "DCP-135C"
 28 "MFC-210C"
 29 "MFC-420CN"
 30 "MFC-410CN"
 31 "MFC-620CN"
 32 "MFC-610CLN"
 33 "MFC-620CLN"
 34 "DCP-110C"
 35 "DCP-310CN"
 36 "MFC-5440CN"
 37 "MFC-5840CN"
 38 "MFC-3240C"
 39 "MFC-3340CN"
 40 "MFC-7420"
 41 "MFC-7820N"
 42 "DCP-7010"
 43 "DCP-7020"
 44 "DCP-7025"
 45 "MFC-7220"
 46 "MFC-7225N"
 47 "MFC-9420CN"
 48 "DCP-8060"
 49 "DCP-8065DN"
 50 "MFC-8460N"
 51 "MFC-8860DN"
 52 "MFC-8870DW"
 53 "MFC-8660DN"
 54 "DCP-115C"
 55 "DCP-116C"
 56 "DCP-117C"
 57 "DCP-118C"
 58 "DCP-120C"
 59 "DCP-315CN"
 60 "DCP-340CW"
 61 "MFC-215C"
 62 "MFC-425CN"
 63 "MFC-820CW"
 64 "MFC-820CN"
 65 "MFC-640CW"
 66 "MFC-615CL"
 67 "MFC-830CLN"
 68 "MFC-840CLN"
 69 "DCP-130C"
 70 "DCP-330C"
 71 "DCP-540CN"
 72 "MFC-240C"
 73 "DCP-750CW"
 74 "MFC-440CN"
 75 "MFC-660CN"
 76 "MFC-665CW"
 77 "MFC-845CW"
 78 "MFC-460CN"
 79 "MFC-630CD"
 80 "MFC-850CDN"
 81 "MFC-5460CN"
 82 "MFC-5860CN"
 83 "MFC-3360C"
 84 "DCP-750CN"
 85 "MFC-860CDN"

Devices on network
  0 juliet              "MFC-5440CN"        N:BRN_JULIET
ping
test juliet
ping BRN_JULIET -w 10

PING juliet (192.168.1.50) 56(84) bytes of data.
64 bytes from juliet (192.168.1.50): icmp_seq=1 ttl=60 time=7.16 ms
64 bytes from juliet (192.168.1.50): icmp_seq=2 ttl=60 time=3.37 ms
64 bytes from juliet (192.168.1.50): icmp_seq=3 ttl=60 time=3.41 ms
64 bytes from juliet (192.168.1.50): icmp_seq=4 ttl=60 time=6.45 ms
64 bytes from juliet (192.168.1.50): icmp_seq=5 ttl=60 time=3.42 ms
64 bytes from juliet (192.168.1.50): icmp_seq=6 ttl=60 time=3.35 ms
64 bytes from juliet (192.168.1.50): icmp_seq=7 ttl=60 time=3.43 ms
64 bytes from juliet (192.168.1.50): icmp_seq=8 ttl=60 time=3.35 ms
64 bytes from juliet (192.168.1.50): icmp_seq=9 ttl=60 time=3.41 ms
64 bytes from juliet (192.168.1.50): icmp_seq=10 ttl=60 time=3.34 ms

--- juliet ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9000ms
rtt min/avg/max/mdev = 3.345/4.073/7.167/1.380 ms

```

This is sane's debugging info
# export SANE_DEBUG_DLL=128
# scanimage -L
```
[sanei_debug] Setting debug level of dll to 128.
[dll] sane_init: SANE dll backend version 1.0.12 from sane-backends 1.0.19
[dll] sane_init/read_dlld: processing /etc/sane.d/dll.d ...
[dll] sane_init/read_dlld: considering /etc/sane.d/dll.d/hplip
[dll] sane_init/read_config: reading dll.d/hplip
[dll] add_backend: adding backend `hpaio'
[dll] sane_init/read_dlld: done.
[dll] sane_init/read_config: reading dll.conf
[dll] add_backend: adding backend `net'
[dll] add_backend: adding backend `abaton'
[dll] add_backend: adding backend `agfafocus'
[dll] add_backend: adding backend `apple'
[dll] add_backend: adding backend `avision'
[dll] add_backend: adding backend `artec'
[dll] add_backend: adding backend `artec_eplus48u'
[dll] add_backend: adding backend `as6e'
[dll] add_backend: adding backend `bh'
[dll] add_backend: adding backend `canon'
[dll] add_backend: adding backend `canon630u'
[dll] add_backend: adding backend `cardscan'
[dll] add_backend: adding backend `coolscan'
[dll] add_backend: adding backend `coolscan2'
[dll] add_backend: adding backend `dell1600n_net'
[dll] add_backend: adding backend `dmc'
[dll] add_backend: adding backend `epjitsu'
[dll] add_backend: adding backend `epson'
[dll] add_backend: adding backend `fujitsu'
[dll] add_backend: adding backend `genesys'
[dll] add_backend: adding backend `gt68xx'
[dll] add_backend: adding backend `hp'
[dll] add_backend: adding backend `hp3900'
[dll] add_backend: adding backend `hpsj5s'
[dll] add_backend: adding backend `hp3500'
[dll] add_backend: adding backend `hp4200'
[dll] add_backend: adding backend `hp5400'
[dll] add_backend: adding backend `hp5590'
[dll] add_backend: adding backend `hpljm1005'
[dll] add_backend: adding backend `hs2p'
[dll] add_backend: adding backend `ibm'
[dll] add_backend: adding backend `leo'
[dll] add_backend: adding backend `lexmark'
[dll] add_backend: adding backend `ma1509'
[dll] add_backend: adding backend `matsushita'
[dll] add_backend: adding backend `microtek'
[dll] add_backend: adding backend `microtek2'
[dll] add_backend: adding backend `mustek'
[dll] add_backend: adding backend `mustek_usb'
[dll] add_backend: adding backend `mustek_usb2'
[dll] add_backend: adding backend `nec'
[dll] add_backend: adding backend `niash'
[dll] add_backend: adding backend `pie'
[dll] add_backend: adding backend `pixma'
[dll] add_backend: adding backend `plustek'
[dll] add_backend: adding backend `qcam'
[dll] add_backend: adding backend `ricoh'
[dll] add_backend: adding backend `s9036'
[dll] add_backend: adding backend `sceptre'
[dll] add_backend: adding backend `sharp'
[dll] add_backend: adding backend `sm3600'
[dll] add_backend: adding backend `sm3840'
[dll] add_backend: adding backend `snapscan'
[dll] add_backend: adding backend `sp15c'
[dll] add_backend: adding backend `tamarack'
[dll] add_backend: adding backend `teco1'
[dll] add_backend: adding backend `teco2'
[dll] add_backend: adding backend `teco3'
[dll] add_backend: adding backend `u12'
[dll] add_backend: adding backend `umax'
[dll] add_backend: adding backend `umax1220u'
[dll] add_backend: adding backend `v4l'
[dll] sane_get_devices
[dll] load: searching backend `v4l' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-v4l.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-v4l.so.1'
[dll] init: initializing backend `v4l'
[dll] init: backend `v4l' is version 1.0.4
[dll] load: searching backend `umax1220u' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-umax1220u.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-umax1220u.so.1'
[dll] init: initializing backend `umax1220u'
[dll] init: backend `umax1220u' is version 1.0.1
[dll] load: searching backend `umax' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-umax.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-umax.so.1'
[dll] init: initializing backend `umax'
[dll] init: backend `umax' is version 1.0.45
[dll] load: searching backend `u12' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-u12.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-u12.so.1'
[dll] init: initializing backend `u12'
[dll] init: backend `u12' is version 1.0.0
[dll] load: searching backend `teco3' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-teco3.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-teco3.so.1'
[dll] init: initializing backend `teco3'
[dll] init: backend `teco3' is version 1.0.1
[dll] load: searching backend `teco2' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-teco2.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-teco2.so.1'
[dll] init: initializing backend `teco2'
[dll] init: backend `teco2' is version 1.0.10
[dll] load: searching backend `teco1' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-teco1.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-teco1.so.1'
[dll] init: initializing backend `teco1'
[dll] init: backend `teco1' is version 1.0.10
[dll] load: searching backend `tamarack' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-tamarack.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-tamarack.so.1'
[dll] init: initializing backend `tamarack'
[dll] init: backend `tamarack' is version 1.0.0
[dll] load: searching backend `sp15c' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-sp15c.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-sp15c.so.1'
[dll] init: initializing backend `sp15c'
[dll] init: backend `sp15c' is version 1.0.0
[dll] load: searching backend `snapscan' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-snapscan.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-snapscan.so.1'
[dll] init: initializing backend `snapscan'
[dll] init: backend `snapscan' is version 1.4.53
[dll] load: searching backend `sm3840' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-sm3840.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-sm3840.so.1'
[dll] init: initializing backend `sm3840'
[dll] init: backend `sm3840' is version 1.0.0
[dll] load: searching backend `sm3600' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-sm3600.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-sm3600.so.1'
[dll] init: initializing backend `sm3600'
[dll] init: backend `sm3600' is version 1.0.6
[dll] load: searching backend `sharp' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-sharp.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-sharp.so.1'
[dll] init: initializing backend `sharp'
[dll] init: backend `sharp' is version 1.0.0
[dll] load: searching backend `sceptre' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-sceptre.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-sceptre.so.1'
[dll] init: initializing backend `sceptre'
[dll] init: backend `sceptre' is version 1.0.10
[dll] load: searching backend `s9036' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-s9036.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-s9036.so.1'
[dll] init: initializing backend `s9036'
[dll] init: backend `s9036' is version 1.0.0
[dll] load: searching backend `ricoh' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-ricoh.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-ricoh.so.1'
[dll] init: initializing backend `ricoh'
[dll] init: backend `ricoh' is version 1.0.0
[dll] load: searching backend `qcam' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-qcam.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-qcam.so.1'
[dll] init: initializing backend `qcam'
[dll] init: backend `qcam' is version 1.0.0
[dll] load: searching backend `plustek' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-plustek.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-plustek.so.1'
[dll] init: initializing backend `plustek'
[dll] init: backend `plustek' is version 1.0.0
[dll] load: searching backend `pixma' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-pixma.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-pixma.so.1'
[dll] init: initializing backend `pixma'
[dll] init: backend `pixma' is version 1.0.13
[dll] load: searching backend `pie' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-pie.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-pie.so.1'
[dll] init: initializing backend `pie'
[dll] init: backend `pie' is version 1.0.9
[dll] load: searching backend `niash' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-niash.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-niash.so.1'
[dll] init: initializing backend `niash'
[dll] init: backend `niash' is version 1.0.1
[dll] load: searching backend `nec' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-nec.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-nec.so.1'
[dll] init: initializing backend `nec'
[dll] init: backend `nec' is version 1.0.0
[dll] load: searching backend `mustek_usb2' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-mustek_usb2.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-mustek_usb2.so.1'
[dll] init: initializing backend `mustek_usb2'
[dll] init: backend `mustek_usb2' is version 1.0.10
[dll] load: searching backend `mustek_usb' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-mustek_usb.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-mustek_usb.so.1'
[dll] init: initializing backend `mustek_usb'
[dll] init: backend `mustek_usb' is version 1.0.18
[dll] load: searching backend `mustek' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-mustek.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-mustek.so.1'
[dll] init: initializing backend `mustek'
[dll] init: backend `mustek' is version 1.0.138
[dll] load: searching backend `microtek2' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-microtek2.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-microtek2.so.1'
[dll] init: initializing backend `microtek2'
[dll] init: backend `microtek2' is version 1.0.0
[dll] load: searching backend `microtek' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-microtek.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-microtek.so.1'
[dll] init: initializing backend `microtek'
[dll] init: backend `microtek' is version 1.0.0
[dll] load: searching backend `matsushita' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-matsushita.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-matsushita.so.1'
[dll] init: initializing backend `matsushita'
[dll] init: backend `matsushita' is version 1.0.7
[dll] load: searching backend `ma1509' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-ma1509.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-ma1509.so.1'
[dll] init: initializing backend `ma1509'
[dll] init: backend `ma1509' is version 1.0.3
[dll] load: searching backend `lexmark' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-lexmark.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-lexmark.so.1'
[dll] init: initializing backend `lexmark'
[dll] init: backend `lexmark' is version 1.0.19
[dll] load: searching backend `leo' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-leo.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-leo.so.1'
[dll] init: initializing backend `leo'
[dll] init: backend `leo' is version 1.0.11
[dll] load: searching backend `ibm' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-ibm.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-ibm.so.1'
[dll] init: initializing backend `ibm'
[dll] init: backend `ibm' is version 1.0.0
[dll] load: searching backend `hs2p' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-hs2p.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-hs2p.so.1'
[dll] init: initializing backend `hs2p'
[dll] init: backend `hs2p' is version 1.0.0
[dll] load: searching backend `hpljm1005' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-hpljm1005.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-hpljm1005.so.1'
[dll] init: initializing backend `hpljm1005'
[dll] init: backend `hpljm1005' is version 1.0.0
[dll] load: searching backend `hp5590' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-hp5590.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-hp5590.so.1'
[dll] init: initializing backend `hp5590'
[dll] init: backend `hp5590' is version 1.0.2
[dll] load: searching backend `hp5400' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-hp5400.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-hp5400.so.1'
[dll] init: initializing backend `hp5400'
[dll] init: backend `hp5400' is version 1.0.3
[dll] load: searching backend `hp4200' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-hp4200.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-hp4200.so.1'
[dll] init: initializing backend `hp4200'
[dll] init: backend `hp4200' is version 1.0.0
[dll] load: searching backend `hp3500' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-hp3500.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-hp3500.so.1'
[dll] init: initializing backend `hp3500'
[dll] init: backend `hp3500' is version 1.0.0
[dll] load: searching backend `hpsj5s' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-hpsj5s.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-hpsj5s.so.1'
[dll] init: initializing backend `hpsj5s'
[dll] init: backend `hpsj5s' is version 1.0.3
[dll] load: searching backend `hp3900' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-hp3900.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-hp3900.so.1'
[dll] init: initializing backend `hp3900'
[dll] init: backend `hp3900' is version 1.0.0
[dll] load: searching backend `hp' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-hp.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-hp.so.1'
[dll] init: initializing backend `hp'
[dll] init: backend `hp' is version 1.0.8
[dll] load: searching backend `gt68xx' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-gt68xx.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-gt68xx.so.1'
[dll] init: initializing backend `gt68xx'
[dll] init: backend `gt68xx' is version 1.0.84
[dll] load: searching backend `genesys' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-genesys.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-genesys.so.1'
[dll] init: initializing backend `genesys'
[dll] init: backend `genesys' is version 1.0.9
[dll] load: searching backend `fujitsu' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-fujitsu.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-fujitsu.so.1'
[dll] init: initializing backend `fujitsu'
[dll] init: backend `fujitsu' is version 1.0.55
[dll] load: searching backend `epson' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-epson.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-epson.so.1'
[dll] init: initializing backend `epson'
[dll] init: backend `epson' is version 1.0.247
[dll] load: searching backend `epjitsu' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-epjitsu.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-epjitsu.so.1'
[dll] init: initializing backend `epjitsu'
[dll] init: backend `epjitsu' is version 1.0.10
[dll] load: searching backend `dmc' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-dmc.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-dmc.so.1'
[dll] init: initializing backend `dmc'
[dll] init: backend `dmc' is version 1.0.0
[dll] load: searching backend `dell1600n_net' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-dell1600n_net.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-dell1600n_net.so.1'
[dll] init: initializing backend `dell1600n_net'
[dll] init: backend `dell1600n_net' is version 1.0.0
[dll] load: searching backend `coolscan2' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-coolscan2.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-coolscan2.so.1'
[dll] init: initializing backend `coolscan2'
[dll] init: backend `coolscan2' is version 1.0.0
[dll] load: searching backend `coolscan' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-coolscan.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-coolscan.so.1'
[dll] init: initializing backend `coolscan'
[dll] init: backend `coolscan' is version 1.0.0
[dll] load: searching backend `cardscan' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-cardscan.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-cardscan.so.1'
[dll] init: initializing backend `cardscan'
[dll] init: backend `cardscan' is version 1.0.0
[dll] load: searching backend `canon630u' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-canon630u.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-canon630u.so.1'
[dll] init: initializing backend `canon630u'
[dll] init: backend `canon630u' is version 1.0.1
[dll] load: searching backend `canon' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-canon.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-canon.so.1'
[dll] init: initializing backend `canon'
[dll] init: backend `canon' is version 1.0.0
[dll] load: searching backend `bh' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-bh.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-bh.so.1'
[dll] init: initializing backend `bh'
[dll] init: backend `bh' is version 1.0.4
[dll] load: searching backend `as6e' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-as6e.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-as6e.so.1'
[dll] init: initializing backend `as6e'
[dll] load: searching backend `artec_eplus48u' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-artec_eplus48u.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-artec_eplus48u.so.1'
[dll] init: initializing backend `artec_eplus48u'
[dll] init: backend `artec_eplus48u' is version 1.0.0
[dll] load: searching backend `artec' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-artec.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-artec.so.1'
[dll] init: initializing backend `artec'
[dll] init: backend `artec' is version 1.0.0
[dll] load: searching backend `avision' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-avision.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-avision.so.1'
[dll] init: initializing backend `avision'
[dll] init: backend `avision' is version 1.0.264
[dll] load: searching backend `apple' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-apple.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-apple.so.1'
[dll] init: initializing backend `apple'
[dll] init: backend `apple' is version 1.0.0
[dll] load: searching backend `agfafocus' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-agfafocus.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-agfafocus.so.1'
[dll] init: initializing backend `agfafocus'
[dll] init: backend `agfafocus' is version 1.0.0
[dll] load: searching backend `abaton' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-abaton.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-abaton.so.1'
[dll] init: initializing backend `abaton'
[dll] init: backend `abaton' is version 1.0.0
[dll] load: searching backend `net' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-net.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-net.so.1'
[dll] init: initializing backend `net'
[dll] init: backend `net' is version 1.0.19
[dll] load: searching backend `hpaio' in `/usr/lib/sane'
[dll] load: trying to load `/usr/lib/sane/libsane-hpaio.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-hpaio.so.1'
[dll] init: initializing backend `hpaio'
[dll] init: backend `hpaio' is version 1.0.0
[dll] sane_get_devices: found 0 devices

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
[dll] sane_exit: exiting
[dll] sane_exit: calling backend `v4l's exit function
[dll] sane_exit: calling backend `umax1220u's exit function
[dll] sane_exit: calling backend `umax's exit function
[dll] sane_exit: calling backend `u12's exit function
[dll] sane_exit: calling backend `teco3's exit function
[dll] sane_exit: calling backend `teco2's exit function
[dll] sane_exit: calling backend `teco1's exit function
[dll] sane_exit: calling backend `tamarack's exit function
[dll] sane_exit: calling backend `sp15c's exit function
[dll] sane_exit: calling backend `snapscan's exit function
[dll] sane_exit: calling backend `sm3840's exit function
[dll] sane_exit: calling backend `sm3600's exit function
[dll] sane_exit: calling backend `sharp's exit function
[dll] sane_exit: calling backend `sceptre's exit function
[dll] sane_exit: calling backend `s9036's exit function
[dll] sane_exit: calling backend `ricoh's exit function
[dll] sane_exit: calling backend `qcam's exit function
[dll] sane_exit: calling backend `plustek's exit function
[dll] sane_exit: calling backend `pixma's exit function
[dll] sane_exit: calling backend `pie's exit function
[dll] sane_exit: calling backend `niash's exit function
[dll] sane_exit: calling backend `nec's exit function
[dll] sane_exit: calling backend `mustek_usb2's exit function
[dll] sane_exit: calling backend `mustek_usb's exit function
[dll] sane_exit: calling backend `mustek's exit function
[dll] sane_exit: calling backend `microtek2's exit function
[dll] sane_exit: calling backend `microtek's exit function
[dll] sane_exit: calling backend `matsushita's exit function
[dll] sane_exit: calling backend `ma1509's exit function
[dll] sane_exit: calling backend `lexmark's exit function
[dll] sane_exit: calling backend `leo's exit function
[dll] sane_exit: calling backend `ibm's exit function
[dll] sane_exit: calling backend `hs2p's exit function
[dll] sane_exit: calling backend `hpljm1005's exit function
[dll] sane_exit: calling backend `hp5590's exit function
[dll] sane_exit: calling backend `hp5400's exit function
[dll] sane_exit: calling backend `hp4200's exit function
[dll] sane_exit: calling backend `hp3500's exit function
[dll] sane_exit: calling backend `hpsj5s's exit function
[dll] sane_exit: calling backend `hp3900's exit function
[dll] sane_exit: calling backend `hp's exit function
[dll] sane_exit: calling backend `gt68xx's exit function
[dll] sane_exit: calling backend `genesys's exit function
[dll] sane_exit: calling backend `fujitsu's exit function
[dll] sane_exit: calling backend `epson's exit function
[dll] sane_exit: calling backend `epjitsu's exit function
[dll] sane_exit: calling backend `dmc's exit function
[dll] sane_exit: calling backend `dell1600n_net's exit function
[dll] sane_exit: calling backend `coolscan2's exit function
[dll] sane_exit: calling backend `coolscan's exit function
[dll] sane_exit: calling backend `cardscan's exit function
[dll] sane_exit: calling backend `canon630u's exit function
[dll] sane_exit: calling backend `canon's exit function
[dll] sane_exit: calling backend `bh's exit function
[dll] sane_exit: calling backend `artec_eplus48u's exit function
[dll] sane_exit: calling backend `artec's exit function
[dll] sane_exit: calling backend `avision's exit function
[dll] sane_exit: calling backend `apple's exit function
[dll] sane_exit: calling backend `agfafocus's exit function
[dll] sane_exit: calling backend `abaton's exit function
[dll] sane_exit: calling backend `net's exit function
[dll] sane_exit: calling backend `hpaio's exit function
[dll] sane_exit: finished
```


I have removed and reinstalled sane & xsane and that did not help.  I have removed the printer configuration and reinstalled it.  That did not help.

Any ideas?

---

### Post by muzzamo on 2008-05-02
There is a note about problems with brother drivers in 8.04 on the brother linux website.

[http://ubuntuforums.org/showpost.php...6&postcount=12](http://ubuntuforums.org/showpost.php...6&postcount=12)

Did that help at all?

---

### Post by ipawlov on 2008-05-02
Hi,

I got the same problem, but my DCP-135C is connected on local USB. I detected that after upgrade there was no /etc/udev/rules.d/45-libsane.rules more. So I created this and inserted the following lines:

# Brother DCP-135C
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="01ce", MODE="666", GROUP="scanner"

LABEL="libsane_rules_end"

after getting the propriate data with lsusb.

Now it is working fine printing and scanning like in 7.10

---

### Post by jpeach on 2008-05-02
> **muzzamo said:**
> There is a note about problems with brother drivers in 8.04 on the brother linux website.

[http://ubuntuforums.org/showpost.php...6&postcount=12](http://ubuntuforums.org/showpost.php...6&postcount=12)

Did that help at all?

muzzamo, can you please check that link.  It does not take me to where you are suggesting.  Thanks

---

### Post by surfcity_dad on 2008-05-03
I believe this is the URL noted in a previous post, I've also copied the content.  

[http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#143](http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#143)

# Ubuntu 8.04 does not have /usr/share/cups/model directory where our driver create a ppd file.
Please follow the instruction below when the installation failed with the message about it.

1. Uninstall the cupswrapper driver.
Command : sudo dpkg -P (driver name)

2. Create /usr/share/cups/model directory
Command : sudo mkdir /usr/share/cups/model

3. Install the cupswrapper driver
Command : sudo dpkg -i --force-all --force-architecture (driver file name)

---

### Post by geekATlarge on 2008-05-04
jpeach, have you fixed your problem? is it a generic network problem? I encountered a generic network problem after my upgrade and posted a fix as [http://ubuntuforums.org/showthread.php?t=781744](http://ubuntuforums.org/showthread.php?t=781744)

---

### Post by jpeach on 2008-05-06
The scanner part is working again.  What got it working was to remove the driver for the scanner and reinstall it.  This worked on the 32bit and 64amd machines.

There are two drivers depending on the model of Brother device that you have (brscan and brscan2).  To determine which one you have installed, issue the following command from the command prompt
 
```
dpkg -l | grep brscan
```

For me it gave the following output.  The second column is the name of the driver.  If you do not get any output then you do not have the driver installed.  That is alright as the next step will remove the driver.  Skip it and continue with the rest

```
ii  brscan2         0.2.4        Brother Scanner Driver
```

In my case it is the brscan2.  You can also check by looking at the [scanner drive page]("http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html") on the Brother site.

Now remove the old driver (brscan2):

```
sudo apt-get remove brscan2
```

or, if your driver was brscan 

```
sudo apt-get remove brscan
```

During the removal of the driver on my machine, the following errors were reported.  It is safe to ignore them.

```
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ALL': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/AL': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane': No such file or directory

```

Now that the driver is removed, the next step is to download and install the driver.  [Brother's scanner page]("http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html") contains the drivers for 32 and 64 bit versions of Debian (Red Hat / Mandriva (Mandrake) / SuSE / FedoraCore are also on that page, ignore them).  Download the driver for your hardware, there are several to choose from.

To install the driver use the following command
```
sudo dpkg -i brscan2-0.2.4-0.amd64.deb
```

Make sure you replace the brscan2-0.2.4-0.amd64.deb with the name of the file that you download.  The one shown here is the brscan2 driver for amd64 hardware

The last step is to configure the scanner to work with your system.  The Brother [scanner page]("http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html") has links to how to configure the scanner based on how it is connected (USB or Network) and the driver.  On the instruction pages follow the ones for debian.  In my case I am using a network printer located at 192.168.1.50 and I want to call it juliet.  The command was:
```
sudo brsaneconfig2 -a name=juliet model=MFC-5440CN ip=192.168.1.50
```

---

### Post by jpeach on 2008-05-06
surfcity_dad, thanks that fixed the problem.

---

### Post by Fernando Negro on 2008-05-09
(wrong thread, can't delete this message, ignore it)

---

### Post by Statik on 2008-06-17
I too now have a MFC-440CN which worked in 7.04 but now doesn't function. I've tried changing from socket://<IP>:9100 to lpd://<IP>/binary_p1, no joy, then switching to the built-in Brother drivers with synaptec, still no go. Printer doesn't even show the job arriving. Can still ping the printer.

Worth mentioning that its a Trendnet wireless router hard connected to the printer and wirelessly connected to the laptop.

Any ideas?

Statik

---

### Post by jpeach on 2008-06-17
Statik, I was able to get it to work by completely reinstalling the drivers again (I upgraded to Hardy instead of a fresh install).  Have you tried that?

---

### Post by Statik on 2008-06-17
When I used synaptic, it uninstalled the previous Brother drivers and installed the new ones. That's the only uninstalling I did.

Which drivers did you use that eventually worked for you?

Statik

---

### Post by jpeach on 2008-06-18
Statik, I used the drivers and followed the directions on the Brother's linux driver page.  Let me know if you need the URL for that as I can try and find it again.

---

### Post by theozzlives on 2008-09-25
I have that problem with a Mustek 1200 CU, except mine is a USB shared over the network to my Laptop. It worked fine in 7.10, but the second I upgraded to 8.04, nothing.

---

### Post by ohme on 2008-10-20
I did both your suggestion and the suggestion from the brother site.
I don't know which of them worked because they both failed at the beginning, before I did 1 more obvious step - 
plug and unplug the scanner (:

thanks.

> **jpeach said:**
> The scanner part is working again.  What got it working was to remove the driver for the scanner and reinstall it.  This worked on the 32bit and 64amd machines.

There are two drivers depending on the model of Brother device that you have (brscan and brscan2).  To determine which one you have installed, issue the following command from the command prompt
 
```
dpkg -l | grep brscan
```

For me it gave the following output.  The second column is the name of the driver.  If you do not get any output then you do not have the driver installed.  That is alright as the next step will remove the driver.  Skip it and continue with the rest

```
ii  brscan2         0.2.4        Brother Scanner Driver
```

In my case it is the brscan2.  You can also check by looking at the [scanner drive page]("http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html") on the Brother site.

Now remove the old driver (brscan2):

```
sudo apt-get remove brscan2
```

or, if your driver was brscan 

```
sudo apt-get remove brscan
```

During the removal of the driver on my machine, the following errors were reported.  It is safe to ignore them.

```
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ALL': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/AL': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane': No such file or directory

```

Now that the driver is removed, the next step is to download and install the driver.  [Brother's scanner page]("http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html") contains the drivers for 32 and 64 bit versions of Debian (Red Hat / Mandriva (Mandrake) / SuSE / FedoraCore are also on that page, ignore them).  Download the driver for your hardware, there are several to choose from.

To install the driver use the following command
```
sudo dpkg -i brscan2-0.2.4-0.amd64.deb
```

Make sure you replace the brscan2-0.2.4-0.amd64.deb with the name of the file that you download.  The one shown here is the brscan2 driver for amd64 hardware

The last step is to configure the scanner to work with your system.  The Brother [scanner page]("http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html") has links to how to configure the scanner based on how it is connected (USB or Network) and the driver.  On the instruction pages follow the ones for debian.  In my case I am using a network printer located at 192.168.1.50 and I want to call it juliet.  The command was:
```
sudo brsaneconfig2 -a name=juliet model=MFC-5440CN ip=192.168.1.50
```

---

### Post by davidwhthomas on 2009-08-27
I found xsane needed to run as root:

I solved by running

```
sudo xsane
```

from the terminal and running as root.

You may be able to run as your regular user after following the install instructions here:

[http://solutions.brother.com/linux/sol/printer/linux/sane_install.html](http://solutions.brother.com/linux/sol/printer/linux/sane_install.html)

---

### Post by emmiesix on 2009-11-07
jpeach, your fix worked for me for my MFC-7440N after updgrade to 9.10 knocked out the scanner.  Thanks!

---

### Post by jpeach on 2011-11-12
When I upgraded to 11.10 (64-bit) I had the same problem getting my MFG-5440CN to be detected.  It turns out that this is a known problem and Brother covers the solution in its FAQ.
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101)

In my case, using brscan2, I used the following commands as root.

```
cd /usr/lib
ln -s ../lib64/libbrscandec2.so.1.0.0 .
ln -s ../lib64/libbrcolm2.so.1.0.1 .
ln -s ../lib64/libbrcolm2.so .
ln -s ../lib64/libbrscandec2.so.1 .
ln -s ../lib64/libbrscandec2.so .
ln -s ../lib64/libbrcolm2.so.1
cd sane
ln -s ../../lib64/sane/libsane-brother2.so.1.0.7 .
ln -s ../../lib64/sane/libsane-brother2.so.1 .
ln -s ../../lib64/sane/libsane-brother2.so .
```

Now my scanner is detected and working again.

---

### Post by oldos2er on 2011-11-13
Closed, please don't bump old threads.

---

