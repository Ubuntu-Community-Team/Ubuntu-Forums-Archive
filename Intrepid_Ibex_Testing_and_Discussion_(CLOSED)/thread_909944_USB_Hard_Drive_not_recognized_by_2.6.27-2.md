---
title: "USB Hard Drive not recognized by 2.6.27-2"
date: 2008-09-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by sddfdds on 2008-09-04
I updated to 2.6.27-2 today, and one of my hard drives is no longer recognized.  It is in a Vantec NexStar GX enclosure, and was working fine on .26, and continues to work fine on a Hardy machine.  Here is the dmesg for it:

```
[ 6722.944029] usb 5-5: new high speed USB device using ehci_hcd and address 27
[ 6723.077863] usb 5-5: configuration #1 chosen from 1 choice
[ 6723.079511] hub 5-5:1.0: USB hub found
[ 6723.080345] hub 5-5:1.0: 4 ports detected
[ 6732.712034] usb 5-5: reset high speed USB device using ehci_hcd and address 27
[ 6733.124011] usb 5-5.1: new high speed USB device using ehci_hcd and address 28
[ 6733.364598] usb 5-5.1: configuration #1 chosen from 1 choice
[ 6733.365180] scsi17 : SCSI emulation for USB Mass Storage devices
[ 6733.365818] usb-storage: device found at 28
[ 6733.365830] usb-storage: waiting for device to settle before scanning
[ 6738.364276] usb-storage: device scan complete
[ 6738.361002] scsi 17:0:0:0: Direct-Access     ST340063 2A               3.04 PQ: 0 ANSI: 0
[ 6738.361002] sd 17:0:0:0: [sdm] 781422769 512-byte hardware sectors (400088 MB)
[ 6738.361002] sd 17:0:0:0: [sdm] Write Protect is off
[ 6738.361002] sd 17:0:0:0: [sdm] Mode Sense: 03 00 00 00
[ 6738.361002] sd 17:0:0:0: [sdm] Assuming drive cache: write through
[ 6738.361002] sd 17:0:0:0: [sdm] 781422769 512-byte hardware sectors (400088 MB)
[ 6738.370354] sd 17:0:0:0: [sdm] Write Protect is off
[ 6738.370362] sd 17:0:0:0: [sdm] Mode Sense: 03 00 00 00
[ 6738.370365] sd 17:0:0:0: [sdm] Assuming drive cache: write through
[ 6738.371516]  sdm: sdm1
[ 6738.418089] sd 17:0:0:0: [sdm] Attached SCSI disk
[ 6738.418995] sd 17:0:0:0: Attached scsi generic sg8 type 0
[ 6738.656598] sd 17:0:0:0: [sdm] Sense Key : No Sense [current] 
[ 6738.656614] sd 17:0:0:0: [sdm] Add. Sense: No additional sense information
```

From there, the ```
[ 6738.656598] sd 17:0:0:0: [sdm] Sense Key : No Sense [current] 
[ 6738.656614] sd 17:0:0:0: [sdm] Add. Sense: No additional sense information
``` repeats endlessly.

The 4 port hub that is a part of the enclosure continues to work fine though, with a floppy drive, a printer, and another hard drive.  I have a Vantec NexStar 3 enclosure as well, and it is working just fine.  Dmesg for the working enclosure:

```
[ 4281.996024] usb 5-3: new high speed USB device using ehci_hcd and address 19
[ 4282.131863] usb 5-3: configuration #1 chosen from 1 choice
[ 4282.133222] scsi12 : SCSI emulation for USB Mass Storage devices
[ 4282.133561] usb-storage: device found at 19
[ 4282.133566] usb-storage: waiting for device to settle before scanning
[ 4287.132002] usb-storage: device scan complete
[ 4287.136004] scsi 12:0:0:0: Direct-Access     ST375064 0AS                   PQ: 0 ANSI: 2
[ 4287.138368] sd 12:0:0:0: [sdi] 1465149168 512-byte hardware sectors (750156 MB)
[ 4287.144790] sd 12:0:0:0: [sdi] Write Protect is off
[ 4287.144800] sd 12:0:0:0: [sdi] Mode Sense: 38 00 00 00
[ 4287.144804] sd 12:0:0:0: [sdi] Assuming drive cache: write through
[ 4287.152388] sd 12:0:0:0: [sdi] 1465149168 512-byte hardware sectors (750156 MB)
[ 4287.154966] sd 12:0:0:0: [sdi] Write Protect is off
[ 4287.154975] sd 12:0:0:0: [sdi] Mode Sense: 38 00 00 00
[ 4287.154979] sd 12:0:0:0: [sdi] Assuming drive cache: write through
[ 4287.154988]  sdi: sdi1
[ 4287.176965] sd 12:0:0:0: [sdi] Attached SCSI disk
[ 4287.177173] sd 12:0:0:0: Attached scsi generic sg7 type 0
[ 4289.129138] kjournald starting.  Commit interval 5 seconds
[ 4289.130101] EXT3 FS on sdi1, internal journal
[ 4289.130110] EXT3-fs: mounted filesystem with ordered data mode.
```


Is there anything I can do to fix this, or do I just need to file a bug?

Thanks

---

### Post by sddfdds on 2008-09-04
Bug reported here

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264789](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264789)

---

### Post by sintacto on 2008-09-10
when i plug in my 80gig usb drive (ext3 format) 
processor goes to 100% and does not mount 
dmesg:  
[  777.047443] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
[  777.048563] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
[  777.048574] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
[  777.049806] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
[  777.049817] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
[  777.051061] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
[  777.051071] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
[  777.052326] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
[  777.052339] sd 4:0:0:0: [sdb] Add. Sense: No additional sense in


fat32 drives still work

this ext3 usb hard drive still works with 7.01 just to make sure it wasnt the hd goin bad.

---

