---
title: "USB-disk is fine, kernel has a hard time"
date: 2010-04-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by dusdus on 2010-04-20
Hi there,

I have a LaCie 500Gb USB-drive. The disk is formatted as NTFS and works fine on several other pc's/ laptops with windows > XP.

In Lucid however, it gives me troubles. It simply disappears, even while accessing the drive (playing an mp3 eg.).

kern.log is flooded with
```

Apr 20 17:18:21 laptux kernel: [29441.850051] usb 6-2: new full speed USB device using uhci_hcd and address 14
Apr 20 17:18:21 laptux kernel: [29441.972564] usb 6-2: device descriptor read/64, error -32
Apr 20 17:18:22 laptux kernel: [29442.212548] usb 6-2: device descriptor read/64, error -32
Apr 20 17:18:22 laptux kernel: [29442.442472] usb 6-2: new full speed USB device using uhci_hcd and address 15
Apr 20 17:18:22 laptux kernel: [29442.570723] usb 6-2: device descriptor read/64, error -32
Apr 20 17:18:22 laptux kernel: [29442.800087] usb 6-2: device descriptor read/64, error -32
Apr 20 17:18:22 laptux kernel: [29443.030119] usb 6-2: new full speed USB device using uhci_hcd and address 16
Apr 20 17:18:23 laptux kernel: [29443.063147] usb 6-2: device descriptor read/8, error -71
Apr 20 17:18:23 laptux kernel: [29443.201155] usb 6-2: device descriptor read/8, error -71
Apr 20 17:18:23 laptux kernel: [29443.430102] usb 6-2: new full speed USB device using uhci_hcd and address 17
Apr 20 17:18:23 laptux kernel: [29443.460166] usb 6-2: device descriptor read/8, error -71
Apr 20 17:18:23 laptux kernel: [29443.601165] usb 6-2: device descriptor read/8, error -71
Apr 20 17:18:23 laptux kernel: [29443.710107] hub 6-0:1.0: unable to enumerate USB device on port 2

```

There's a bug-report, I guess it's about the same problem [https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/433438](https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/433438)

Though there someone said:
```

The latest Lucid updates (3/2/2010) have eliminated this issue for me. The AMD64 kernel version 2.6.32-14 and the x86 kernel 2.6.32-15 and their associated modules are no longer experiencing this error.

```

I'm pretty sure I'm up-to-date, running the 2.6.32-21 kernel.
Does anyone have a solution for it? I'm not sure what to do. Or should I simply wait and send the developers cookies? :)

---

### Post by dusdus on 2010-04-21
ok, probably no one else here is getting this or knows anything, so I'll just focus on the bugreport

---

