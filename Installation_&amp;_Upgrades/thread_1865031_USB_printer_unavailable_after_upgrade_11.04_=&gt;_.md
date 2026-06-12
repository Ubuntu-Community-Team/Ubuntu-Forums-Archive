---
title: "USB printer unavailable after upgrade 11.04 =&gt; 11.10"
date: 2011-10-19
forum: Installation &amp; Upgrades
---

### Post by fcodvpt on 2011-10-19
Hi,

Since the upgrade 11.04 => 11.10 on Sunday, my printer (Canon MG 5150) is not available.

In the printer properties, I have the following message if I try to print a test page :

```

Printer cable not connected or printer power off; will retry in 30 seconds...

```

Here is what appear with dmesg when I power the printer on :

```

$ dmesg
...
[   59.728061] usb 1-2: new high speed USB device number 5 using ehci_hcd
[   59.866122] scsi8 : usb-storage 1-2:1.2
[   60.865977] scsi 8:0:0:0: Direct-Access     Canon    MG5100 series    0101 PQ: 0 ANSI: 2
[   60.936259] sd 8:0:0:0: Attached scsi generic sg6 type 0
[   60.942146] sd 8:0:0:0: [sdf] Attached SCSI removable disk
[   61.281092] usb 1-2: usbfs: interface 2 claimed by usb-storage while 'usb' sets config #1
[   61.282553] usb 1-2: usbfs: process 2117 (usb) did not claim interface 0 before use

```

The upgrades have not solved the problem.

Any suggestion ?

Regards

---

### Post by cdoebbler on 2011-11-22
Same problem neither the printer nor the scanner works. I finally install cups and printer began to work, but still not the scanner. 

I have tried three scanners with Ubuntu scanner utility (IRIScan Anywhere 2, which is a piece of junk, but did not work; Canon MG5150, and old TWAIN Microtek Scanner. None worked. Hope Ubuntu (Canonical) can find a solution to this aggravating problem.

---

