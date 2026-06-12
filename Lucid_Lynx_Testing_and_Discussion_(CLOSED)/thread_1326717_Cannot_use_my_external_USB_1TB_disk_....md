---
title: "Cannot use my external USB 1TB disk ..."
date: 2009-11-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zika on 2009-11-14
Up to today I was able to use my external 1TB Fujitsu-Siemens disk. Today when I tried it cannot mount. I tried it on Karmic on another machine: it works. I tried it on Vista on both machine and it works. I was using it yesterday since, for example, my music is on it. It is with only one partition (NTFS) ... Any ideas what could have caused this problem?

---

### Post by VMC on 2009-11-14
> **zika said:**
> Up to today I was able to use my external 1TB Fujitsu-Siemens disk. Today when I tried it cannot mount. I tried it on Karmic on another machine: it works. I tried it on Vista on both machine and it works. I was using it yesterday since, for example, my music is on it. It is with only one partition (NTFS) ... Any ideas what could have caused this problem?

Does the system recognize the drive( fdisk -l)? How about the Disk Utility. What does it show? Or lsusb output.

---

### Post by zika on 2009-11-15
> **VMC said:**
> Does the system recognize the drive( fdisk -l)? How about the Disk Utility. What does it show? Or lsusb output.Today it is recognized. I'll have to see what today's upgrade brought or whatever changed and report back. I'm confused ... I tried everything yesterday and it did not work. Thank You for Your response ...
```
~$ sudo fdisk -l
   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1      121602   976759808    7  HPFS/NTFS
```
```
~$ sudo lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 08bb:2706 Texas Instruments Japan 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 152d:2329 JMicron Technology Corp. / JMicron USA Technology Corp. 
Bus 001 Device 003: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by zika on 2009-11-15
It's not mounting again. Just a few hours later after boot I get (from dmesg):```
[  133.395202] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[  133.396565] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[  133.396570]  sdb: sdb1
[  133.416187] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[  133.416191] sd 8:0:0:0: [sdb] Attached SCSI disk
[  141.172535] usb 1-2: reset high speed USB device using ehci_hcd and address 5
[  150.160019] usb 1-2: reset high speed USB device using ehci_hcd and address 5
[  151.539238] sd 8:0:0:0: [sdb] Unhandled sense code
[  151.539242] sd 8:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  151.539246] sd 8:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  151.539250] sd 8:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  151.539254] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 08 00 00 00 f0 00
[  151.539261] end_request: I/O error, dev sdb, sector 2048
[  151.539266] __ratelimit: 20 callbacks suppressed
[  151.539269] Buffer I/O error on device sdb1, logical block 0
[  151.539276] Buffer I/O error on device sdb1, logical block 1
[  151.539279] Buffer I/O error on device sdb1, logical block 2
[  151.539282] Buffer I/O error on device sdb1, logical block 3
[  151.539284] Buffer I/O error on device sdb1, logical block 4
[  151.539286] Buffer I/O error on device sdb1, logical block 5
[  151.539289] Buffer I/O error on device sdb1, logical block 6
[  151.539291] Buffer I/O error on device sdb1, logical block 7
[  151.539293] Buffer I/O error on device sdb1, logical block 8
[  151.539296] Buffer I/O error on device sdb1, logical block 9
```

If I try to disconnect it from mains supply and reconnect I get:```
[  481.557444] usb 1-2: USB disconnect, address 6
[ 1352.242532] usb 1-2: new high speed USB device using ehci_hcd and address 7
[ 1352.393440] usb 1-2: configuration #1 chosen from 1 choice
[ 1352.394320] scsi10 : SCSI emulation for USB Mass Storage devices
[ 1352.394457] usb-storage: device found at 7
[ 1352.394459] usb-storage: waiting for device to settle before scanning
[ 1357.390239] usb-storage: device scan complete
[ 1357.390706] scsi 10:0:0:0: Direct-Access     Hitachi  HDT721010SLA360       PQ: 0 ANSI: 2 CCS
[ 1357.391486] sd 10:0:0:0: Attached scsi generic sg2 type 0
[ 1357.393743] sd 10:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[ 1357.394697] sd 10:0:0:0: [sdb] Write Protect is off
[ 1357.394702] sd 10:0:0:0: [sdb] Mode Sense: 34 00 00 00
[ 1357.394704] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[ 1357.398132] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[ 1357.398138]  sdb: sdb1
[ 1357.414312] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[ 1357.414316] sd 10:0:0:0: [sdb] Attached SCSI disk
```
and drive is, still not visible.

Any ideas? It works in Vista and in Karmic, on a laptop.

---

### Post by cariboo on 2009-11-15
Is /dev/sdb1 not your external drive? From the looks of it, it is being detected, just not auto-mounted. Can you mount it manually?

---

### Post by zika on 2009-11-15
> **cariboo907 said:**
> Is /dev/sdb1 not your external drive? From the looks of it, it is being detected, just not auto-mounted. Can you mount it manually?I've discovered that I have to (for whatever reason) /dev/sdf1 to mount. /dev/sdb1 doesn't work. But it, still, doesn't mount automatically. Thank You.
Update: After reboot (just to test it it will survive and mount again, unmount-ing before reboot) I get (note that now It has to be /dev/sdb1, not /dev/sdf1)```
~$ sudo mount -t ntfs /dev/sdb1 /media/zika
Error reading bootsector: Input/output error
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
```After I was stubborn and did the same mount again it works. Beats me ...
The only reason I formatted it in NTFS is that it would be more mobile that way. Silly me ...

---

