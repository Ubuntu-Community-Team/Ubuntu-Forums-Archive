---
title: "Ubuntu Lucid not mounting usb Hard Drive that works in other distros (Karmic, Jaunty)"
date: 2010-03-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Niej on 2010-03-29
Hi, I have Lucid beta1 installed and a funny thing is that
I cannot mount my external Samsung S2 500gb external usb Hard Drive.
I can mount it on Jaunty, Karmic, win Xp. The disc **is not corrupted**.
Also, when trying to mount it on win 7 it ask to format it. (yes, it is win 7).
When trying to mount it on Lucid it says it is inconsistent and that
chkdsk /f should be run on it.
**Thing that I did several times, and returns no error!**
the "chkdsk found no error message"
The output that I've received so far:
```

sudo mount -t ntfs /dev/sdb1 /media/Samsung/
Error reading bootsector: Input/output error
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

```.
Ntfsfix says:
```

sudo ntfsfix /dev/sdb1
Mounting volume... Error reading bootsector: Input/output error.
Failed to startup volume: Input/output error.
FAILED
Attempting to correct errors... Error opening partition device: No such file or directory.
FAILED
Failed to startup volume: No such file or directory.
Volume is corrupt. You should run chkdsk.


```
It appears in lsusb
```

Bus 002 Device 013: ID 04e8:1f05 Samsung Electronics Co., Ltd 
Bus 002 Device 003: ID 0461:4d2f Primax Electronics, Ltd 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0489:e00f Foxconn / Hon Hai 
Bus 001 Device 003: ID 064e:2100 Suyin Corp. 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```
The Karmic Live cd mounts it without problems, in the same machine.
Sony Vaio F series.
I will appreciate any suggestions.
Thanks in advance!
Seba
PD:
Also dmesg:
```

 1783.017595] sd 6:0:0:0: [sdb] Unhandled error code
[ 1783.017600] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
[ 1783.017606] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 3f 00 00 08 00
[ 1783.017622] end_request: I/O error, dev sdb, sector 63
[ 1783.017630] Buffer I/O error on device sdb1, logical block 0
[ 1783.017637] Buffer I/O error on device sdb1, logical block 1
[ 1783.017642] Buffer I/O error on device sdb1, logical block 2
[ 1783.017647] Buffer I/O error on device sdb1, logical block 3
[ 1783.017729] usb 2-1.5: USB disconnect, address 4
[ 1783.017783] sd 6:0:0:0: rejecting I/O to offline device
[ 1783.017818] sd 6:0:0:0: rejecting I/O to offline device
[ 1783.340493] usb 2-1.5: new high speed USB device using ehci_hcd and address 5
[ 1783.452153] usb 2-1.5: configuration #1 chosen from 1 choice
[ 1783.453376] scsi7 : SCSI emulation for USB Mass Storage devices
[ 1783.453584] usb-storage: device found at 5
[ 1783.453589] usb-storage: waiting for device to settle before scanning
[ 1788.443804] usb-storage: device scan complete
[ 1788.486165] scsi 7:0:0:0: Direct-Access     S-Line   S2 Portable           PQ: 0 ANSI: 2 CCS
[ 1788.487800] sd 7:0:0:0: Attached scsi generic sg2 type 0
[ 1788.561599] sd 7:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[ 1788.563139] sd 7:0:0:0: [sdb] Write Protect is off
[ 1788.563146] sd 7:0:0:0: [sdb] Mode Sense: 34 00 00 00
[ 1788.563151] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 1788.565161] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 1788.565169]  sdb: sdb1
[ 1789.014265] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 1789.014274] sd 7:0:0:0: [sdb] Attached SCSI disk
[ 1797.187371] usb 2-1.5: reset high speed USB device using ehci_hcd and address 5
[ 1828.256292] usb 2-1.5: reset high speed USB device using ehci_hcd and address 5
[ 1828.286866] sd 7:0:0:0: Device offlined - not ready after error recovery
[ 1828.286880] sd 7:0:0:0: [sdb] Unhandled error code
[ 1828.286885] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
[ 1828.286891] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 3f 00 00 20 00
[ 1828.286907] end_request: I/O error, dev sdb, sector 63
[ 1828.286915] Buffer I/O error on device sdb1, logical block 0
[ 1828.286922] Buffer I/O error on device sdb1, logical block 1
[ 1828.286927] Buffer I/O error on device sdb1, logical block 2
[ 1828.286932] Buffer I/O error on device sdb1, logical block 3
[ 1828.286943] Buffer I/O error on device sdb1, logical block 4
[ 1828.286948] Buffer I/O error on device sdb1, logical block 5
[ 1828.286953] Buffer I/O error on device sdb1, logical block 6
[ 1828.286957] Buffer I/O error on device sdb1, logical block 7
[ 1828.286962] Buffer I/O error on device sdb1, logical block 8
[ 1828.286967] Buffer I/O error on device sdb1, logical block 9
[ 1828.286990] sd 7:0:0:0: rejecting I/O to offline device
[ 1828.287003] sd 7:0:0:0: rejecting I/O to offline device
[ 1828.287017] sd 7:0:0:0: rejecting I/O to offline device
[ 1828.287033] sd 7:0:0:0: rejecting I/O to offline device
[ 1828.287054] usb 2-1.5: USB disconnect, address 5
[ 1828.556158] usb 2-1.5: new high speed USB device using ehci_hcd and address 6
[ 1828.667931] usb 2-1.5: configuration #1 chosen from 1 choice
[ 1828.669133] scsi8 : SCSI emulation for USB Mass Storage devices
[ 1828.669500] usb-storage: device found at 6
[ 1828.669504] usb-storage: waiting for device to settle before scanning
[ 1833.662813] usb-storage: device scan complete
[ 1833.705316] scsi 8:0:0:0: Direct-Access     S-Line   S2 Portable           PQ: 0 ANSI: 2 CCS
[ 1833.706615] sd 8:0:0:0: Attached scsi generic sg2 type 0
[ 1833.780107] sd 8:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[ 1833.781306] sd 8:0:0:0: [sdb] Write Protect is off
[ 1833.781313] sd 8:0:0:0: [sdb] Mode Sense: 34 00 00 00
[ 1833.781318] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 1833.783062] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 1833.783070]  sdb: sdb1
[ 1834.254198] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 1834.254206] sd 8:0:0:0: [sdb] Attached SCSI disk
[ 1842.250482] usb 2-1.5: reset high speed USB device using ehci_hcd and address 6
[ 1850.241458] usb 2-1.5: reset high speed USB device using ehci_hcd and address 6
[ 1881.075357] sd 8:0:0:0: Device offlined - not ready after error recovery
[ 1881.075372] sd 8:0:0:0: [sdb] Unhandled error code
[ 1881.075376] sd 8:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
[ 1881.075383] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 3f 00 00 08 00
[ 1881.075398] end_request: I/O error, dev sdb, sector 63
[ 1881.075405] __ratelimit: 6 callbacks suppressed
[ 1881.075410] Buffer I/O error on device sdb1, logical block 0
[ 1881.075417] Buffer I/O error on device sdb1, logical block 1
[ 1881.075422] Buffer I/O error on device sdb1, logical block 2
[ 1881.075427] Buffer I/O error on device sdb1, logical block 3
[ 1881.075514] usb 2-1.5: USB disconnect, address 6
[ 1881.075575] sd 8:0:0:0: rejecting I/O to offline device
[ 1881.075610] sd 8:0:0:0: rejecting I/O to offline device
[ 1881.364066] usb 2-1.5: new high speed USB device using ehci_hcd and address 7
[ 1881.471942] usb 2-1.5: configuration #1 chosen from 1 choice
[ 1881.473182] scsi9 : SCSI emulation for USB Mass Storage devices
[ 1881.473382] usb-storage: device found at 7
[ 1881.473386] usb-storage: waiting for device to settle before scanning
[ 1886.466865] usb-storage: device scan complete
[ 1886.509340] scsi 9:0:0:0: Direct-Access     S-Line   S2 Portable           PQ: 0 ANSI: 2 CCS
[ 1886.511658] sd 9:0:0:0: Attached scsi generic sg2 type 0
[ 1886.585372] sd 9:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[ 1886.586656] sd 9:0:0:0: [sdb] Write Protect is off
[ 1886.586663] sd 9:0:0:0: [sdb] Mode Sense: 34 00 00 00
[ 1886.586668] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[ 1886.588811] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[ 1886.588821]  sdb: sdb1
[ 1887.033274] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[ 1887.033284] sd 9:0:0:0: [sdb] Attached SCSI disk
[ 1895.091037] usb 2-1.5: reset high speed USB device using ehci_hcd and address 7
[ 1903.085599] usb 2-1.5: reset high speed USB device using ehci_hcd and address 7
[ 1934.125442] sd 9:0:0:0: Device offlined - not ready after error recovery
[ 1934.125455] sd 9:0:0:0: [sdb] Unhandled error code
[ 1934.125459] sd 9:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
[ 1934.125466] sd 9:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 3f 00 00 08 00
[ 1934.125481] end_request: I/O error, dev sdb, sector 63
[ 1934.125489] Buffer I/O error on device sdb1, logical block 0
[ 1934.125496] Buffer I/O error on device sdb1, logical block 1
[ 1934.125501] Buffer I/O error on device sdb1, logical block 2
[ 1934.125506] Buffer I/O error on device sdb1, logical block 3
[ 1934.125563] sd 9:0:0:0: rejecting I/O to offline device
[ 1934.125612] usb 2-1.5: USB disconnect, address 7
[ 1934.125687] sd 9:0:0:0: rejecting I/O to offline device
[ 1934.125709] sd 9:0:0:0: rejecting I/O to offline device
[ 1934.428166] usb 2-1.5: new high speed USB device using ehci_hcd and address 8
[ 1934.539403] usb 2-1.5: configuration #1 chosen from 1 choice
[ 1934.540628] scsi10 : SCSI emulation for USB Mass Storage devices
[ 1934.540831] usb-storage: device found at 8
[ 1934.540836] usb-storage: waiting for device to settle before scanning
[ 1939.540888] usb-storage: device scan complete
[ 1939.583259] scsi 10:0:0:0: Direct-Access     S-Line   S2 Portable           PQ: 0 ANSI: 2 CCS
[ 1939.584786] sd 10:0:0:0: Attached scsi generic sg2 type 0
[ 1939.658475] sd 10:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[ 1939.660086] sd 10:0:0:0: [sdb] Write Protect is off
[ 1939.660093] sd 10:0:0:0: [sdb] Mode Sense: 34 00 00 00
[ 1939.660098] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[ 1939.662129] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[ 1939.662137]  sdb: sdb1
[ 1940.132312] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[ 1940.132320] sd 10:0:0:0: [sdb] Attached SCSI disk
[ 1947.998865] usb 2-1.5: reset high speed USB device using ehci_hcd and address 8
[ 1956.992798] usb 2-1.5: reset high speed USB device using ehci_hcd and address 8
[ 1987.878784] sd 10:0:0:0: Device offlined - not ready after error recovery
[ 1987.878796] sd 10:0:0:0: [sdb] Unhandled error code
[ 1987.878801] sd 10:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
[ 1987.878807] sd 10:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 3f 00 00 08 00
[ 1987.878823] end_request: I/O error, dev sdb, sector 63
[ 1987.878831] Buffer I/O error on device sdb1, logical block 0
[ 1987.878838] Buffer I/O error on device sdb1, logical block 1
[ 1987.878843] Buffer I/O error on device sdb1, logical block 2
[ 1987.878847] Buffer I/O error on device sdb1, logical block 3
[ 1987.878967] sd 10:0:0:0: rejecting I/O to offline device
[ 1987.878979] usb 2-1.5: USB disconnect, address 8
[ 1987.879018] sd 10:0:0:0: rejecting I/O to offline device
[ 1987.879038] sd 10:0:0:0: rejecting I/O to offline device
[ 1987.879055] sd 10:0:0:0: rejecting I/O to offline device
[ 1988.181752] usb 2-1.5: new high speed USB device using ehci_hcd and address 9
[ 1988.293222] usb 2-1.5: configuration #1 chosen from 1 choice
[ 1988.294476] scsi11 : SCSI emulation for USB Mass Storage devices
[ 1988.294696] usb-storage: device found at 9
[ 1988.294700] usb-storage: waiting for device to settle before scanning
[ 1993.284824] usb-storage: device scan complete
[ 1993.327429] scsi 11:0:0:0: Direct-Access     S-Line   S2 Portable           PQ: 0 ANSI: 2 CCS
[ 1993.329661] sd 11:0:0:0: Attached scsi generic sg2 type 0
[ 1993.403954] sd 11:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[ 1993.405291] sd 11:0:0:0: [sdb] Write Protect is off
[ 1993.405298] sd 11:0:0:0: [sdb] Mode Sense: 34 00 00 00
[ 1993.405303] sd 11:0:0:0: [sdb] Assuming drive cache: write through
[ 1993.407145] sd 11:0:0:0: [sdb] Assuming drive cache: write through
[ 1993.407153]  sdb: sdb1
[ 1993.871915] sd 11:0:0:0: [sdb] Assuming drive cache: write through
[ 1993.871922] sd 11:0:0:0: [sdb] Attached SCSI disk
[ 2002.138544] usb 2-1.5: reset high speed USB device using ehci_hcd and address 9
[ 2010.133080] usb 2-1.5: reset high speed USB device using ehci_hcd and address 9
[ 2041.057017] sd 11:0:0:0: Device offlined - not ready after error recovery
[ 2041.057030] sd 11:0:0:0: [sdb] Unhandled error code
[ 2041.057035] sd 11:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
[ 2041.057042] sd 11:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 3f 00 00 08 00
[ 2041.057057] end_request: I/O error, dev sdb, sector 63
[ 2041.057065] Buffer I/O error on device sdb1, logical block 0
[ 2041.057072] Buffer I/O error on device sdb1, logical block 1
[ 2041.057077] Buffer I/O error on device sdb1, logical block 2
[ 2041.057082] Buffer I/O error on device sdb1, logical block 3
[ 2041.057119] usb 2-1.5: USB disconnect, address 9
[ 2041.057129] sd 11:0:0:0: rejecting I/O to offline device
[ 2041.057142] sd 11:0:0:0: rejecting I/O to offline device
[ 2041.057153] sd 11:0:0:0: rejecting I/O to offline device
[ 2041.057163] sd 11:0:0:0: rejecting I/O to offline device
[ 2041.057203] sd 11:0:0:0: rejecting I/O to offline device
[ 2041.057214] sd 11:0:0:0: rejecting I/O to offline device
[ 2041.415666] usb 2-1.5: new high speed USB device using ehci_hcd and address 10
[ 2041.527447] usb 2-1.5: configuration #1 chosen from 1 choice
[ 2041.528483] scsi12 : SCSI emulation for USB Mass Storage devices
[ 2041.528698] usb-storage: device found at 10
[ 2041.528702] usb-storage: waiting for device to settle before scanning
[ 2046.518842] usb-storage: device scan complete
[ 2046.561164] scsi 12:0:0:0: Direct-Access     S-Line   S2 Portable           PQ: 0 ANSI: 2 CCS
[ 2046.562738] sd 12:0:0:0: Attached scsi generic sg2 type 0
[ 2046.636319] sd 12:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[ 2046.637951] sd 12:0:0:0: [sdb] Write Protect is off
[ 2046.637963] sd 12:0:0:0: [sdb] Mode Sense: 34 00 00 00
[ 2046.637973] sd 12:0:0:0: [sdb] Assuming drive cache: write through
[ 2046.639962] sd 12:0:0:0: [sdb] Assuming drive cache: write through
[ 2046.639971]  sdb: sdb1
[ 2047.091279] sd 12:0:0:0: [sdb] Assuming drive cache: write through
[ 2047.091288] sd 12:0:0:0: [sdb] Attached SCSI disk
[ 2055.106062] usb 2-1.5: reset high speed USB device using ehci_hcd and address 10
[ 2063.097254] usb 2-1.5: reset high speed USB device using ehci_hcd and address 10


```

---

### Post by Sef on 2010-03-29
Moved to Lucid.

---

### Post by zeroseven0183 on 2010-03-29
I have a similar problem with my WD My Passport. It used to automount in Karmic but not in Lucid.
However, I was able to force mount it using Storage Device Manager.

Nevertheless, this must be fixed

---

### Post by Niej on 2010-03-29
Thanks for the tip.
I also used Storage Device Manager but I was unable to mount
the disk. It appears as sdb (/dev/sdb) but no options are available.
Forcing mount didn't work either.
It's so weird, and all my working data is in that disk
Seba

---

### Post by garvinrick4 on 2010-03-29
I can mount mine with Code:

sudo mount /dev/sda2 /media/OS

given that my partition is sda2 and it is labeled OS

Mounts in all versions.

---

### Post by Niej on 2010-03-29
Well, when using mount /dev/sdb /media/Samsung, the system
asks to specify the filesystem. So I have to add -t ntfs giving this
all previous results encountered before.
Seba

---

### Post by garvinrick4 on 2010-03-29
> **Niej said:**
> Well, when using mount /dev/sdb /media/Samsung, the system
asks to specify the filesystem. So I have to add -t ntfs giving this
all previous results encountered before.
Seba What is the label of your partition. Here are mine. If does not show one go into gparted and label. Then they all
open sudo mount /dev/sdax /media/whatever your label (x is your partition.)

sudo blkid    


rick@rick-laptop:~$ sudo blkid
/dev/sda1: LABEL="SYSTEM" UUID="EC587B18587AE0AE" TYPE="ntfs" 
/dev/sda2: LABEL="OS" UUID="7C2064AB20646E58" TYPE="ntfs" 
/dev/sda4: LABEL="RECOVERY" UUID="524C43ED4C43CB05" TYPE="ntfs" 
/dev/sda5: LABEL="lucid" UUID="1fa6b366-0d18-442c-91cb-506460b1b9ab" TYPE="ext4" 
/dev/sda6: UUID="904f3813-9702-4940-ac21-33bdcbd44644" TYPE="swap" 
/dev/sda7: LABEL="karmic" UUID="203e3621-e1e0-4879-a286-4736cb8b9b54" TYPE="ext4" 
/dev/sda8: UUID="0db6108c-150d-4466-928e-ef68b4ac2ceb" TYPE="swap" 
rick@rick-laptop:~$

---

### Post by garvinrick4 on 2010-03-30
> **Niej said:**
> Well, when using mount /dev/sdb /media/Samsung, the system
asks to specify the filesystem. So I have to add -t ntfs giving this
all previous results encountered before.
SebaMust be sdb1 not sdb for one thing still check your label.

---

### Post by Niej on 2010-03-31
Hi, unfortunately I don't have the disc right now with me, I friend of mine is saving the data and formating it as ext3. (damn ntfs)
Yes, actually it was sdb1, I run it several times, as sdb and sdb1.
It was not listed when running gparted.
it was not showed in fstab either.
I could not try blkid now but thank you for that tip.
When using another laptop with lucid beta, the disc was not auto mounted, but I was able to mount it manually and even run a ntfsfix on it, it was 'ok'. Then, "safely remove drive", plugged into my laptop, and...
again, "NTFS inconsistent, run chkdsk /f, bla bla"
Again, thank you for your support.
Seba

---

### Post by dusdus on 2010-04-02
I´m having exactly the same problem here. Checked my disk in windows and got no problems. Mounting the device in Karmic or any other distro works fine.

Just 5 minutes ago Lucid wouldn´t even boot, got the message: waiting for USB device (or something like that) for 10 minutes.
Also, when trying to mount the device I´m recieving the message posted bij OP:
bla bla
NTFS is either inconsistent, or there is a hardware fault, or it's aSoftRAID/FakeRAID hardware.
bla bla

log gives me:
reset high speed USB device using ehci_hcd and address 2

a couple of times.

I´ll try and see if there´s already a bugreport on this one.

In the mean time...does anyone have a suggestion? (except going back to Karmic hihi)

---

### Post by dusdus on 2010-04-02
Good news and bad news...
Good news is, we´re not the only ones! :)
Some similar reports:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/545588](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/545588)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530227](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530227)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/515023](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/515023)

Bad news is, seems no one has a clue what´s going on. I´ll try and search some more, but I really hope some wizard accidentally clicks on this topic and magically delivers a solution out of his ubuntu/hat!

---

### Post by dusdus on 2010-04-02
My usb drive gets mounted, kernel spits out:
```

Apr  2 10:39:19 laptux kernel: [  655.100066] usb 2-2: new high speed USB device using ehci_hcd and address 2
Apr  2 10:39:19 laptux kernel: [  655.251130] usb 2-2: configuration #1 chosen from 1 choice
Apr  2 10:39:19 laptux kernel: [  655.291090] Initializing USB Mass Storage driver...
Apr  2 10:39:19 laptux kernel: [  655.292137] scsi5 : SCSI emulation for USB Mass Storage devices
Apr  2 10:39:19 laptux kernel: [  655.292265] usbcore: registered new interface driver usb-storage
Apr  2 10:39:19 laptux kernel: [  655.292268] USB Mass Storage support registered.
Apr  2 10:39:24 laptux kernel: [  660.290810] scsi 5:0:0:0: Direct-Access     SAMSUNG  HM500LI               PQ: 0 ANSI: 2 CCS
Apr  2 10:39:24 laptux kernel: [  660.291248] sd 5:0:0:0: Attached scsi generic sg2 type 0
Apr  2 10:39:24 laptux kernel: [  660.292042] sd 5:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Apr  2 10:39:24 laptux kernel: [  660.293919] sd 5:0:0:0: [sdb] Write Protect is off
Apr  2 10:39:24 laptux kernel: [  660.295538]  sdb: sdb1
Apr  2 10:39:24 laptux kernel: [  660.328931] sd 5:0:0:0: [sdb] Attached SCSI disk
Apr  2 10:39:32 laptux kernel: [  668.130083] usb 2-2: reset high speed USB device using ehci_hcd and address 2
Apr  2 10:39:41 laptux kernel: [  677.130084] usb 2-2: reset high speed USB device using ehci_hcd and address 2
Apr  2 10:40:13 laptux kernel: [  709.130071] usb 2-2: reset high speed USB device using ehci_hcd and address 2

```

I can access the drive though and the kernel seems to agree with it, for at least 10 minutes now... :)

---

### Post by dusdus on 2010-04-02
One way to kinda solve it is by changing the max_sectors of the drive. Mine was 240, and the device is sdb, so I changed the X in a b:
sudo sh -c "echo 120 > /sys/block/sdX/device/max_sectors"

---

### Post by Niej on 2010-04-02
Hi, after formating the disc into ext3,...nothing happened!
I checked it in another lucid beta 1 machine, it doesn't mount it
automatically but manually it works, dmesg said "waiting to disc to settle down", and after some seconds it appears on "computer" and then you can mount it.
Strange thing, my lucid mounts automatically a Western Digital usb HD! But no signs of reconciliation with my Samsung S2 portable ubs HD
I would try the last thing suggested.
seba

---

### Post by dusdus on 2010-04-03
As far as I understand it has something to do with the way the kernel communicates with the disk. I'm not an expert, but it seems that the kernel waits for a command, but only gets information, that's why it'll reset the (S)ATA-drive.

---

### Post by yota on 2010-04-03
In my case the problem was in /lib/udev/rules.d/85-hdparm.rules
renaming it to .disabled fixed the issue:
```

sudo mv /lib/udev/rules.d/85-hdparm.rules /lib/udev/rules.d/85-hdparm.rules.disabled

```

see [https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/515023](https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/515023) for reference

---

### Post by Niej on 2010-04-03
It worked perfectly!
I read the thread [https://bugs.launchpad.net/ubuntu/+s...rm/+bug/515023](https://bugs.launchpad.net/ubuntu/+s...rm/+bug/515023)  
thank you!!! ;)
cheers
seba

---

### Post by wiseberg on 2010-04-03
> **Niej said:**
> It worked perfectly!
I read the thread [https://bugs.launchpad.net/ubuntu/+s...rm/+bug/515023](https://bugs.launchpad.net/ubuntu/+s...rm/+bug/515023)  
thank you!!! ;)
cheers
seba

it's works for me 2!!

thanks everyone above~:lolflag:

---

