---
title: "where is xhci-hcd module in new kernels???"
date: 2012-06-19
forum: Installation &amp; Upgrades
---

### Post by aa-hcl on 2012-06-19
Hi,

After upgrading to 3.2.0-24-generic and 3.2.0-25-generic, I found that my USB3.0 EC card stopped recognizing the hot-plug hard drive.

Looking into the modules I found that the module xhci-hcd is not loaded. It is also not present in the kernel modules:

aa@aa-i7:~$ sudo find / -name *xhci?hcd*
/lib/modules/2.6.38-10-generic/kernel/drivers/usb/host/xhci-hcd.ko
/lib/modules/3.0.0-17-generic/kernel/drivers/usb/host/xhci-hcd.ko
/lib/modules/2.6.38-11-generic/kernel/drivers/usb/host/xhci-hcd.ko
/lib/modules/2.6.38-8-generic/kernel/drivers/usb/host/xhci-hcd.ko
/sys/bus/pci/drivers/xhci_hcd
/sys/module/xhci_hcd
/sys/module/xhci_hcd/drivers/pci:xhci_hcd
/proc/irq/47/xhci_hcd
/proc/irq/46/xhci_hcd
/proc/irq/45/xhci_hcd
/proc/irq/44/xhci_hcd
/proc/irq/43/xhci_hcd


Does it mean that xhci-hcd is now incorporated somewhere in the kernel?

Initially I was confused: xhci_hcd is a driver and xhci-hcd is a module. 

May be for this reason my USB3.0 EC card hot-plug is not working?

Many thanks!!!

---

### Post by pmanski on 2012-06-28
I have the same problem. I just bought USB3.0 CF-reader and it doesn't working under Ubuntu 12.04 (Linux 3.2.0-25-generic). This reader works great in Win7.

I didnt checked before, but I also dont have xhci-hcd module

```
#find / -name *xhci?hcd*
/sys/bus/pci/drivers/xhci_hcd
/sys/module/xhci_hcd
/sys/module/xhci_hcd/drivers/pci:xhci_hcd
/proc/irq/47/xhci_hcd
/proc/irq/46/xhci_hcd
/proc/irq/45/xhci_hcd
/proc/irq/44/xhci_hcd
/proc/irq/43/xhci_hcd
```

USB controler in x220:
```
# lspci | grep USB
...
NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
```

Card reader MODECOM CR-Level3:
```
# lsusb
...
Bus 004 Device 005: ID 05e3:0732 Genesys Logic, Inc.
```

Dmesg after connect
```

# dmesg
...
[ 2253.615694] usb 4-1: new SuperSpeed USB device number 6 using xhci_hcd
[ 2253.638880] scsi10 : usb-storage 4-1:1.0
[ 2254.639422] scsi 10:0:0:0: Direct-Access     Generic  STORAGE DEVICE   0542 PQ: 0 ANSI: 0
[ 2254.641497] sd 10:0:0:0: Attached scsi generic sg1 type 0
[ 2254.642784] sd 10:0:0:0: [sdb] Attached SCSI removable disk

```


PROBLEM SOLVED after upgrading kernel to 3.2.0-26-generic

---

