---
title: "I can not see my usb hdd (Seagate expansion portable drive)"
date: 2016-03-28
forum: MINT
---

### Post by dulaver on 2016-03-28
Hallo everyone,

New here, new to Linux..
(English not my first language)

I have been using my [SIZE=3]Seagate expansion portable drive[/SIZE] (usb hdd 1TB) for several months now with [SIZE=3]Linux mint[/SIZE] ([SIZE=3]I have 17.3 Cinnamon 32-bit[/SIZE]) and worked perfectly.

I recently plugged the usb hdd in a Samsung TV and after that it doesn't seem to work when I plug it in my laptop. 
[COLOR=#0000cd]It does not show up anywhere[/COLOR] (except in terminal after the dmesg command).
I tried also on a windows laptop but I had the same problem. I get the sound that something is plugged in but it doesn't show up.

I tried the following command in terminal :
[COLOR=#0000ff][SIZE=3]dmesg | tail -n 20[/SIZE][/COLOR]
 that I found on a thread in ubuntu forums and I got these :

[ 9812.204166] sd 10:0:0:0: [sdb] Sense not available.
[ 9812.328154] sd 10:0:0:0: [sdb] Attached SCSI disk
[ 9812.344524] sd 9:0:0:0: [sdc] Synchronizing SCSI cache
[ 9812.344581] sd 9:0:0:0: [sdc] Synchronize Cache(10) failed: Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 9812.496409] usb 2-5.1: USB disconnect, device number 12
[ 9990.300105] usb 2-5.2: new high-speed USB device number 13 using ehci-pci
[ 9990.454234] usb 2-5.2: New USB device found, idVendor=0bc2, idProduct=2320
[ 9990.454244] usb 2-5.2: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[ 9990.454252] usb 2-5.2: Product: Expansion
[ 9990.454259] usb 2-5.2: Manufacturer: Seagate
[ 9990.454266] usb 2-5.2: SerialNumber: NA4G42V7
[ 9990.454973] usb-storage 2-5.2:1.0: USB Mass Storage device detected
[ 9990.456870] scsi host11: usb-storage 2-5.2:1.0
[ 9991.457060] scsi 11:0:0:0: Direct-Access     Seagate  Expansion        0608 PQ: 0 ANSI: 6
[ 9991.458108] sd 11:0:0:0: Attached scsi generic sg1 type 0
[ 9991.458743] sd 11:0:0:0: [sdb] 1953525167 512-byte logical blocks: (1.00 TB/931 GiB)
[ 9991.459844] sd 11:0:0:0: [sdb] Write Protect is off
[ 9991.459854] sd 11:0:0:0: [sdb] Mode Sense: 4f 00 00 00
[ 9991.461806] sd 11:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[10022.128108] usb 2-5.2: reset high-speed USB device number 13 using ehci-pci

and this : 

[12913.414357] sd 11:0:0:0: [sdb] Add. Sense: Logical unit is in process of becoming ready
[12913.414369] sd 11:0:0:0: [sdb] CDB: 
[12913.414372] Read(10): 28 00 00 00 00 07 00 00 01 00
[12913.414389] blk_update_request: I/O error, dev sdb, sector 7
[12913.414396] Buffer I/O error on dev sdb, logical block 7, async page read
[13094.111863] sd 11:0:0:0: [sdb] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[13094.111878] sd 11:0:0:0: [sdb] Sense Key : Not Ready [current]
[13094.111886] sd 11:0:0:0: [sdb] Add. Sense: Logical unit is in process of becoming ready
[13094.111893] sd 11:0:0:0: [sdb] CDB: 
[13094.111905] Read(10): 28 00 00 00 00 00 00 00 01 00
[13094.111929] blk_update_request: I/O error, dev sdb, sector 0
[13094.111937] Buffer I/O error on dev sdb, logical block 0, async page read
[13101.061696] sd 11:0:0:0: timing out command, waited 180s
[13101.061715] sd 11:0:0:0: [sdb] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[13101.061722] sd 11:0:0:0: [sdb] Sense Key : Not Ready [current]
[13101.061727] sd 11:0:0:0: [sdb] Add. Sense: Logical unit is in process of becoming ready
[13101.061732] sd 11:0:0:0: [sdb] CDB: 
[13101.061736] Read(10): 28 00 00 00 00 01 00 00 01 00
[13101.061754] blk_update_request: I/O error, dev sdb, sector 1
[13101.061762] Buffer I/O error on dev sdb, logical block 1, async page read

can anyone help ?
is it dead or do I have any chance rescuing it ?

thanks in advance anyhow.

---

### Post by howefield on 2016-03-28
Thread moved to the "*MINT*" sub forum.

---

### Post by yancek on 2016-03-28
> I recently plugged the usb hdd in a Samsung TV

Why?  Did you just plug it in an unplug it?  What were you intending to do?

---

### Post by dulaver on 2016-03-29
Pluged it in to watch some film. 
Did so, closed tv and removed it.

---

