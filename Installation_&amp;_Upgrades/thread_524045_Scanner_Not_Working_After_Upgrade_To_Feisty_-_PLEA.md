---
title: "Scanner Not Working After Upgrade To Feisty - PLEASE HELP"
date: 2007-08-12
forum: Installation &amp; Upgrades
---

### Post by clyrrad on 2007-08-12
Last night I upgraded to Feisty from Edgy using the upgrade tool.  All seems to be fine except that I can not scan anymore.  I have a Samsung SCX-4521F which worked perfectly under Edgy.  Now that Fiesty is installed I get errors like "No Scanners Found", "No Scanners Were Identified" etc.....

I did some research and also searched these forums and found lots of reports with Canon scanners having this issue under Feisty - I am wondering if this same issue applies to the Samsung modes as well.

I can see that my scanner is detected by the OS, but none of my scanning apps like scan2pdf etc can see or use the scanner.  The only utility that scans is the "Samsung Unified Driver Conigurator" that is installed with the printer.

Here is the relevant informaiton: 

scanimage -L
```
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
```

sane-find-scanner
```
  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04e8 [Samsung], product=0x3419 [SCX-4x21 Series]) at libusb:002:003
found USB scanner (vendor=0x0bc7, product=0x0004) at libusb:001:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.
```

dmesg
```
[  898.556000] drivers/usb/class/usblp.c: usblp0: on fire
[ 1027.892000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[ 1028.072000] lp0: using parport0 (interrupt-driven).
[ 1069.672000] drivers/usb/class/usblp.c: usblp0: on fire
[ 1277.976000] drivers/usb/class/usblp.c: usblp0: on fire
[ 1367.352000] drivers/usb/class/usblp.c: usblp0: on fire
[ 1468.472000] drivers/usb/class/usblp.c: usblp0: on fire
[ 1713.908000] drivers/usb/class/usblp.c: usblp0: on fire
[ 1879.208000] drivers/usb/class/usblp.c: usblp0: nonzero read/write bulk status received: -71
[ 1879.208000] drivers/usb/class/usblp.c: usblp0: nonzero read/write bulk status received: -71
[ 1879.208000] drivers/usb/class/usblp.c: usblp0: error -71 reading printer status
[ 1879.208000] drivers/usb/class/usblp.c: usblp0: error -71 reading printer status
[ 1879.208000] drivers/usb/class/usblp.c: usblp0: error -71 reading printer status
[ 1879.208000] drivers/usb/class/usblp.c: usblp0: error -71 reading printer status
[ 1879.208000] drivers/usb/class/usblp.c: usblp0: error -71 reading printer status
[ 1879.208000] drivers/usb/class/usblp.c: usblp0: error -71 reading printer status
[ 1879.208000] drivers/usb/class/usblp.c: usblp0: error -71 reading printer status
[ 1879.212000] drivers/usb/class/usblp.c: usblp0: error -71 reading printer status
[ 1879.212000] drivers/usb/class/usblp.c: usblp0: error -71 reading printer status
[ 1879.212000] drivers/usb/class/usblp.c: usblp0: error -71 reading printer status
[ 1879.248000] usb 3-6: USB disconnect, address 5
[ 1879.252000] drivers/usb/class/usblp.c: usblp0: removed
[ 1891.168000] usb 3-6: new high speed USB device using ehci_hcd and address 6
[ 1891.300000] usb 3-6: configuration #1 chosen from 1 choice
[ 1891.300000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 6 if 0 alt 0 proto 2 vid 0x04E8 pid 0x3272
[ 2724.800000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[ 2724.920000] lp0: using parport0 (interrupt-driven).
[ 2725.016000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[ 2725.144000] lp0: using parport0 (interrupt-driven).
[ 2732.852000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[ 2732.980000] lp0: using parport0 (interrupt-driven).
[ 2733.064000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[ 2733.192000] lp0: using parport0 (interrupt-driven).
[ 3297.216000] /dev/vmnet: open called by PID 11014 (vmware-vmx)
[ 3297.216000] device eth0 entered promiscuous mode
[ 3297.216000] audit(1186947961.873:2): dev=eth0 prom=256 old_prom=0 auid=4294967295
[ 3297.216000] bridge-eth0: enabled promiscuous mode
[ 3297.216000] /dev/vmnet: port on hub 0 successfully opened
[ 3297.500000] /dev/vmmon[12141]: host clock rate change request 0 -> 100
[ 3297.500000] /dev/vmmon[12141]: host clock rate change request 100 -> 101
[ 3915.316000] drivers/usb/class/usblp.c: usblp0: on fire
[ 5261.564000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[ 5261.692000] lp0: using parport0 (interrupt-driven).
[ 5261.752000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[ 5261.884000] lp0: using parport0 (interrupt-driven).
[ 5281.888000] drivers/usb/class/usblp.c: usblp0: on fire

```

Can anyone help me to get my scanner working again?

Thanks in advance!

---

### Post by clyrrad on 2007-08-14
bump - anyone?

---

