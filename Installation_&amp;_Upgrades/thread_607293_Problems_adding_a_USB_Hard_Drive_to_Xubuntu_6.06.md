---
title: "Problems adding a USB Hard Drive to Xubuntu 6.06"
date: 2007-11-08
forum: Installation &amp; Upgrades
---

### Post by jamesr on 2007-11-08
Hi All,

I am having problems adding an external USB drive, it is currently an old SEAGATE ide drive (1GB) in a self powered enclosure.

I added a PCI to USB card. That seemed to work OK and I could see the majority of my USB keys, even ones that the linux-usb group say do not work.

But When I add my USB HD drive nothing is seen on the desktop.
Gparted sees the drive but cannot write to it.
Disk utility in Xubuntu sees the drive but does not report its size. Also only seems to see the drive when no or one partitions are available.

```
lsusb
```outputs> jdsci@Tubby:~$ lsusb
Bus 003 Device 002: ID 14cd:6600
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
The device is seen but no translation of the ID code
```
cat /proc/bus/usb/devices
``` outputs> jdsci@Tubby:~$ cat /proc/bus/usb/devices

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 5
B:  Alloc=  0/800 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.15-29-386 ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:01:01.2
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=256ms

T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=14cd ProdID=6600 Rev= 2.01
S:  Manufacturer=Super Top
S:  Product=USB 2.0  IDE DEVICE
S:  SerialNumber=??????????
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  2mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
E:  Ad=81(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.15-29-386 ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:01:01.1
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 3
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.15-29-386 ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:01:01.0
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms
jdsci@Tubby:~$
The device is seen as a Hard Drive but no serial number

Adding  SanDisk USB Key```
lsusb
``` outputs>  lsusb
Bus 003 Device 004: ID 0781:5150 SanDisk Corp. SDCZ2 Cruzer Mini Flash Drive (thin)
Bus 003 Device 002: ID 14cd:6600
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
jdsci@Tubby:~$
 
So the port and card are working ?

```
sudo fdisk -l
```outputs> Disk /dev/sda: 9104 MB, 9104953344 bytes
255 heads, 63 sectors/track, 1106 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         261     2096451   83  Linux
/dev/sda2             262        1106     6787462+   5  Extended
/dev/sda5             517        1106     4739175   83  Linux
/dev/sda6             262         516     2048224+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 4294 MB, 4294007296 bytes
255 heads, 63 sectors/track, 522 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         496     3984088+  83  Linux
/dev/sdb2             497         522      208845    5  Extended
/dev/sdb5             497         522      208813+  82  Linux swap / Solaris

Disk /dev/sdd: 256 MB, 256900608 bytes
16 heads, 32 sectors/track, 979 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         979      250574+   6  FAT16 sees the SanDisk sdd1 but not the hard drive.

Remove SanDisk and repeat previous tests similar results.

```
sudo sg_scan -i
```outputs > jdsci@Tubby:~$ sudo sg_scan -i
/dev/sg0: scsi0 channel=0 id=0 lun=0
    SEAGATE   ST19171W          0024 [rmb=0 cmdq=1 pqual=0 pdev=0x0]
/dev/sg1: scsi0 channel=0 id=1 lun=0
    SEAGATE   ST15230N          0498 [rmb=0 cmdq=1 pqual=0 pdev=0x0]
/dev/sg2: scsi0 channel=0 id=3 lun=0
    ARCHIVE   Python 28388-XXX  4.CM [rmb=1 cmdq=0 pqual=0 pdev=0x1]
/dev/sg3: scsi0 channel=0 id=4 lun=0
    MATSHITA  CD-R   CW-7502    4.10 [rmb=1 cmdq=0 pqual=0 pdev=0x5]
/dev/sg4: scsi5 channel=0 id=0 lun=0 [em]
    Seagate   Technology 1080M   [rmb=0 cmdq=0 pqual=0 pdev=0x0]
Drive is been seen
```
sudo sg_map
```outputs> jdsci@Tubby:~$ sudo sg_map
/dev/sg0  /dev/sda
/dev/sg1  /dev/sdb
/dev/sg2  /dev/nst0
/dev/sg3  /dev/scd0
/dev/sg4  /dev/sdc Drive is sdc
but still not automounted nor manual mount.
```
dmesg |tail
```outputs> [37658.223527] scsi5 : SCSI emulation for USB Mass Storage devices
[37658.228586] usb-storage: device found at 6
[37658.228617] usb-storage: waiting for device to settle before scanning
[37663.228176]   Vendor: Seagate   Model: Technology 1080M  Rev:  0 0
[37663.228286]   Type:   Direct-Access                      ANSI SCSI revision: 00
[37663.232754] SCSI device sdc: 2114180 512-byte hdwr sectors (1082 MB)
[37663.232804] sdc: assuming drive cache: write through
[37663.236714] SCSI device sdc: 2114180 512-byte hdwr sectors (1082 MB)
[37663.236753] sdc: assuming drive cache: write through
[37663.236784]  sdc:<6>sd 5:0:0:0: SCSI error: return code = 0x10070000
[37663.251916] end_request: I/O error, dev sdc, sector 0
[37663.251952] printk: 152 messages suppressed.
[37663.251982] Buffer I/O error on device sdc, logical block 0
[37663.259208] sd 5:0:0:0: SCSI error: return code = 0x10070000
[37663.259243] end_request: I/O error, dev sdc, sector 4
[37663.259273] Buffer I/O error on device sdc, logical block 1
[37663.265586] sd 5:0:0:0: SCSI error: return code = 0x10070000
[37663.265627] end_request: I/O error, dev sdc, sector 0
[37663.265661] Buffer I/O error on device sdc, logical block 0
[37663.272464] sd 5:0:0:0: SCSI error: return code = 0x10070000
[37663.272504] end_request: I/O error, dev sdc, sector 4
[37663.272534] Buffer I/O error on device sdc, logical block 1
[37663.272611]  unable to read partition table
[37663.272945] sd 5:0:0:0: Attached scsi disk sdc
[37663.273386] sd 5:0:0:0: Attached scsi generic sg4 type 0
[37663.284973] usb-storage: device scan complete
[37665.638346] sd 5:0:0:0: SCSI error: return code = 0x10070000
[37665.638410] end_request: I/O error, dev sdc, sector 2114048 but still  mount will not work.
The USB drive works on XP-Pro system.

Sorry about the long post but I have tried to provide as much information as possible.

---

### Post by jamesr on 2007-11-12
I have partially solved the problem by  setting up another system:-

1)  Xubuntu 6.06 still fails not hardware.
2)  Tried drive on another Ubuntu 7.10 works
3)  Changed my system to Ubuntu 7.10 works so not a hardware problem on the 2nd trial system
4)  Installed Ubuntu 7.04 still works
5)  currently installing Xubuntu 7.04. I know that it should be the same as Ubuntu 7.04 but!!!. This works but see comments below.

Most have reported that their problems started when they upgraded to 7.04 but in  my case the problem was solved. Also I noted that the method of mounting was different. The newer software was using pmount and there was no  file > /proc/bus/usb/devicescreated.

I will update this file so the whole saga is recorded. Hopefully somebody from Canonical is looking at these posts.

This may lead to another thread  ie support for Xubuntu LTS and the best way to update.

5A)  I noticed that the 2nd hard drive hdb was also mounted by pmount , I had not set it up to do this and it comes with some weird names. I will be mounting the system correctly using a  fstab set up

---

