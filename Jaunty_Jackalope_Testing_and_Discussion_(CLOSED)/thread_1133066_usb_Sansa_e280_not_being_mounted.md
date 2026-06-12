---
title: "usb: Sansa e280 not being mounted"
date: 2009-04-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by HankB on 2009-04-22
I have just discovered that Jaunty does not mount my USB (Mass storage) MP3 player. The results of plugging it in is:

```
[ 6722.195378] usb 1-2: USB disconnect, address 11
[ 6725.958494] hub 1-0:1.0: unable to enumerate USB device on port 2
[ 6726.166964] hub 1-0:1.0: unable to enumerate USB device on port 2
[ 6726.548117] usb 1-2: new high speed USB device using ehci_hcd and address 15
[ 6726.700358] usb 1-2: configuration #1 chosen from 1 choice
[ 6726.741176] scsi7 : SCSI emulation for USB Mass Storage devices
[ 6726.762682] usb-storage: device found at 15
[ 6726.762697] usb-storage: waiting for device to settle before scanning
[ 6776.132166] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 406
[ 6890.466278] usb 1-2: USB disconnect, address 15
[ 6896.132171] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 406
[ 7016.134056] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 323
[ 7091.452097] hub 1-0:1.0: unable to enumerate USB device on port 2
[ 7091.640402] hub 1-0:1.0: unable to enumerate USB device on port 2
[ 7092.012136] usb 1-2: new high speed USB device using ehci_hcd and address 18
[ 7092.169324] usb 1-2: configuration #1 chosen from 1 choice
[ 7092.178161] scsi8 : SCSI emulation for USB Mass Storage devices
[ 7092.200279] usb-storage: device found at 18
[ 7092.200294] usb-storage: waiting for device to settle before scanning
```

This is with Rockbox running on the MP3 but I get the same results with the factory Sansa firmware. H/W is an Eee PC if that makes a difference.

I have mounted this on my other laptop running Intrepid to make sure it mounts OK (and it does) with the following results from dmesg:


```
[414304.284104] hub 8-0:1.0: unable to enumerate USB device on port 2
[414304.488144] hub 5-0:1.0: unable to enumerate USB device on port 2
[414304.868055] usb 8-2: new high speed USB device using ehci_hcd and address 10
[414305.020071] usb 8-2: configuration #1 chosen from 1 choice
[414305.023022] scsi8 : SCSI emulation for USB Mass Storage devices
[414305.025244] usb-storage: device found at 10
[414305.025254] usb-storage: waiting for device to settle before scanning
[414310.025859] usb-storage: device scan complete
[414310.028100] scsi 8:0:0:0: Direct-Access     Rockbox  Internal
Storage 0.00 PQ: 0 ANSI: 4
[414310.031457] scsi 8:0:0:1: Direct-Access     Rockbox  SD Card Slot
  0.00 PQ: 0 ANSI: 4
[414310.037067] sd 8:0:0:0: [sdb] 15708160 512-byte hardware sectors (8043 MB)
[414310.040435] sd 8:0:0:0: [sdb] Write Protect is off
[414310.040442] sd 8:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[414310.040447] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[414310.050554] sd 8:0:0:0: [sdb] 15708160 512-byte hardware sectors (8043 MB)
[414310.053934] sd 8:0:0:0: [sdb] Write Protect is off
[414310.053944] sd 8:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[414310.053949] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[414310.053958]  sdb: sdb1 sdb2
[414310.064326] sd 8:0:0:0: [sdb] Attached SCSI removable disk
[414310.064545] sd 8:0:0:0: Attached scsi generic sg2 type 0
[414310.073383] sd 8:0:0:1: [sdc] Attached SCSI removable disk
[414310.073538] sd 8:0:0:1: Attached scsi generic sg3 type 0
```

Other than this, I have not had any problems mounting other USB thumb drives. Suggestions on how to resolve this would be most welcome.

Edit: I tried this using a Jaunty RC live CD on another system (Thinkpad T42) and it also did not mount the Sansa. It normally runs Intrepid and mounts the Sansa without difficulty.

Edit-01: I can confirm that this bug still exists with the release - at least when installed on an Eee PC 901. I also found the same bad behavior on eeebuntu 2.0 (based on 8.10 but with a 2.6.28 kernel, so I suspect it is something related to the 2.6.28 kernel.

-hank

If a mod sees this, please move it to the regular forum. I'm now off to study "best practices for reporting a bug."

---

### Post by javaman67 on 2009-04-23
Same issue here.  Oddly enough, if I open Virtualbox with Windows XP installed as a virtual machine, I am able to detect the Sansa e280 and read/write to it.

---

### Post by HankB on 2009-04-23
> **javaman67 said:**
> Same issue here.  Oddly enough, if I open Virtualbox with Windows XP installed as a virtual machine, I am able to detect the Sansa e280 and read/write to it.
Interesting, but not a good solution for a netbook. I've seen the same problem reported at anythingbutipod too. 

I filed a bug report so feel free to add any further information: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/365532](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/365532)

thanks,
hank

---

