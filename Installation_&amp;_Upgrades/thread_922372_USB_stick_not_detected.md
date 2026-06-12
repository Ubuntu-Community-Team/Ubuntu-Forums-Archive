---
title: "USB stick not detected"
date: 2008-09-17
forum: Installation &amp; Upgrades
---

### Post by polarbar on 2008-09-17
:popcorn:

Hi,

I am a rookie with Linux.

I just installed Ubuntu workstation 8.04.1.

When I plug my USB stick to read/write data it is not detected.:(

Strangely, my USB mouse is working fine.:confused:

---

### Post by mkokotovich on 2008-09-17
Open a terminal, and enter ```
lsusb
```Then plug in your USB stick and repeat the command.  Post both outputs.

You should see one additional entry, which would be your USB stick.  If that works, then the system recognizes it.

---

### Post by polarbar on 2008-09-17
desktop:~$ lsusb (without USB stick)
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
desktop:~$ lsusb (with USB stick)
Bus 005 Device 003: ID 090c:6000 Feiya Technology Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
desktop:~$

---

### Post by mkokotovich on 2008-09-17
So it looks like it was recognized.  Now enter```
ls /dev/sd*
```Then plug in the drive, and repeat the command.  Post both outputs.

Then unplug device, and enter```
lshal -m
```Then plug in device, type Ctrl-C in the terminal to stop lshal, then post what was spit out.

---

### Post by polarbar on 2008-09-17
desktop:~$ ls /dev/sd*  (without USB Stick)
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda3  /dev/sda4  /dev/sda5

desktop:~$ ls /dev/sd*  (with USB Stick)
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda3  /dev/sda4  /dev/sda5

desktop:~$ lshal -m  (without USB Stick)

Start monitoring devicelist:
-------------------------------------------------  (with USB Stick)
06:58:22.759: usb_device_90c_6000_12345678901234567890 added
06:58:22.865: usb_device_90c_6000_12345678901234567890_if0 added
06:58:28.446: usb_device_90c_6000_12345678901234567890_if0_scsi_host added
06:58:28.456: usb_device_90c_6000_12345678901234567890_if0_scsi_host_scsi_device_lun0 added

(ctrl-c)

desktop:~$

---

### Post by mkokotovich on 2008-09-17
Hmm, one more thing.  Unplug the stick and run ```
dmesg | tail -20
``` Then plug in the stick and repeat that command. Post both outputs.

Hopefully we can find something useful.

In a normal situation, once you plugged in the stick there should have been a /dev/sdb - but that isn't there.

Actually, one last thing.  Post the following output (doesn't matter where the stick is)```
lsmod | grep usb
```

---

### Post by mrsteveman1 on 2008-09-17
Sometimes it's quicker to just run cat /proc/partitions :D

If you can plug the stick in and not see any new devices in /dev/, or the partitions proc file, or fdisk -l, then something is very wrong, what I'm not sure though.

---

### Post by polarbar on 2008-09-17
desktop:~$ dmesg | tail -20  (without USB stick)
[  610.551903] end_request: I/O error, dev sdb, sector 0
[  610.551905] Buffer I/O error on device sdb, logical block 0
[  610.551912] Dev sdb: unable to read RDB block 0
[  610.551924] sd 5:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  610.551928] end_request: I/O error, dev sdb, sector 0
[  610.551941] Buffer I/O error on device sdb, logical block 0
[  610.552014] sd 5:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  610.552018] end_request: I/O error, dev sdb, sector 0
[  610.552020] Buffer I/O error on device sdb, logical block 0
[  610.552044] sd 5:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  610.552048] end_request: I/O error, dev sdb, sector 24
[  610.552063] sd 5:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  610.552067] end_request: I/O error, dev sdb, sector 24
[  610.552083] sd 5:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  610.552087] end_request: I/O error, dev sdb, sector 0
[  610.552103] sd 5:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  610.552107] end_request: I/O error, dev sdb, sector 0
[  610.552114]  unable to read partition table
[  610.552262] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[  610.552399] sd 5:0:0:0: Attached scsi generic sg2 type 0

desktop:~$ dmesg | tail -20   (with USB stick)
[  610.552262] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[  610.552399] sd 5:0:0:0: Attached scsi generic sg2 type 0
[ 4608.566776] usb 5-7: new high speed USB device using ehci_hcd and address 6
[ 4608.700578] usb 5-7: configuration #1 chosen from 1 choice
[ 4608.702207] scsi6 : SCSI emulation for USB Mass Storage devices
[ 4608.703432] usb-storage: device found at 6
[ 4608.703440] usb-storage: waiting for device to settle before scanning
[ 4613.694290] usb-storage: device scan complete
[ 4614.261966] scsi 6:0:0:0: Direct-Access                               6000 PQ: 0 ANSI: 0 CCS
[ 4614.264472] sd 6:0:0:0: [sdb] 3970048 512-byte hardware sectors (2033 MB)
[ 4614.265346] sd 6:0:0:0: [sdb] Write Protect is off
[ 4614.265354] sd 6:0:0:0: [sdb] Mode Sense: 4b 00 00 08
[ 4614.265357] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 4614.268443] sd 6:0:0:0: [sdb] 3970048 512-byte hardware sectors (2033 MB)
[ 4614.269197] sd 6:0:0:0: [sdb] Write Protect is off
[ 4614.269203] sd 6:0:0:0: [sdb] Mode Sense: 4b 00 00 08
[ 4614.269206] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 4614.269214]  sdb:end_request: I/O error, dev sdb, sector 0
[ 4614.397337] printk: 4 messages suppressed.
[ 4614.397341] Buffer I/O error on device sdb, logical block 0

desktop:~$ lsmod | grep usb 
usb_storage            73664  2 
libusual               19108  1 usb_storage
usbhid                 31872  0 
hid                    38784  1 usbhid
scsi_mod              151436  5 usb_storage,sg,sr_mod,sd_mod,libata
usbcore               146028  6 usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd

desktop:~$

---

### Post by mkokotovich on 2008-09-17
Hmm, that looks like you might have a bad usb stick.  Can you test that on anther computer or test another stick on this one?  It looks like it is detected and mounted correctly, but then an error occurs trying to use it.

---

### Post by polarbar on 2008-09-17
hi mkokotovich:),

I am on dual boot on the workstation:  I have Ubuntu and WinXP_SP3.

So, on the same workstation with XP I see the USB stick!

On another workstation with XP_SP3 I see the stick.

-------------------------------

I am astonish by the SCSI thing in:
desktop:~$ dmesg | tail -20 (with USB stick)

I have no SCSI device on the workstation

When I installed Ubuntu, I saw things like sda (SCSI) partition instead of hda (ide).

Is it part of the problem?

---

### Post by polarbar on 2008-10-11
I have found the problem.


My USB stick works only with Windows!

My USB stick is a SDHC 2GB.
[http://en.wikipedia.org/wiki/Secure_Digital_card](http://en.wikipedia.org/wiki/Secure_Digital_card)

Maybe its a driver problem.

---

### Post by tereensio on 2008-11-05
> **mkokotovich said:**
> So it looks like it was recognized.  Now enter```
ls /dev/sd*
```Then plug in the drive, and repeat the command.  Post both outputs.

Then unplug device, and enter```
lshal -m
```Then plug in device, type Ctrl-C in the terminal to stop lshal, then post what was spit out.

I get this:

tere@zappa:~ $ lsusb
Bus 004 Device 002: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 0951:1607 Kingston Technology Data Traveler 2.0
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
tere@zappa:~ $ ls /dev/sd*
/dev/sda   /dev/sda2  /dev/sda4  /dev/sdc
/dev/sda1  /dev/sda3  /dev/sdb   /dev/sdc1
tere@zappa:~ $ ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda3  /dev/sda4  /dev/sdb
tere@zappa:~ $ lshal -m

Start monitoring devicelist:
-------------------------------------------------
^C
tere@zappa:~ $ lshal -m

Start monitoring devicelist:
-------------------------------------------------
^C
tere@zappa:~ $ 

So what to do next?

---

### Post by tereensio on 2008-11-06
> **tereensio said:**
> I get this:

tere@zappa:~ $ lsusb
Bus 004 Device 002: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 0951:1607 Kingston Technology Data Traveler 2.0
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
tere@zappa:~ $ ls /dev/sd*
/dev/sda   /dev/sda2  /dev/sda4  /dev/sdc
/dev/sda1  /dev/sda3  /dev/sdb   /dev/sdc1
tere@zappa:~ $ ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda3  /dev/sda4  /dev/sdb
tere@zappa:~ $ lshal -m

Start monitoring devicelist:
-------------------------------------------------
^C
tere@zappa:~ $ lshal -m

Start monitoring devicelist:
-------------------------------------------------
^C
tere@zappa:~ $ 

So what to do next?

This is on 8.10

---

### Post by mkokotovich on 2008-11-11
Your output is confusing, once you plugged your drive in you had less disks?

Maybe you did something backwards.  Let's try again.

Without the flashdrive plugged in, type ls -l /dev/disk/by-id

Plug in the drive

Type ls -l /dev/disk/by-id

Post both those outputs.

Unplug your drive

Type lshal -m

Plug in your drive

Wait at least 15 seconds

Unplug your drive

Then post the output.

---

### Post by tereensio on 2008-11-11
Thanks;

something has happened, because now the stick is being detected. I have a problem with my soundcard, which also is not found, and have been de-installing and re-installing stuff, which seems to have accidentally cured the usb stick problem but not the soundcard problem. :)

---

