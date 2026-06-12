---
title: "NooElec NESDR Mini 2 RTL2832U + RT820T2"
date: 2015-08-23
forum: MINT
---

### Post by chris_w4 on 2015-08-23
Hello Everyone,

I just purchased a NooElec NESDR Mini 2 that uses a RTL2832U with a RT820T2 tuner. I am trying to use w_scan and Kaffeine but I cannot scan any TV channels at all! I can access the SDR and get audio fine. Any help would be appreciated! I am using Linux Mint 17.2 (not trying to upset anyone but it's based on ubuntu so I couldn't think of any better place to get help)

```
dmesg output:
usb 3-5: new high-speed USB device number 3 using ehci-pci
usb 3-5: New USB device found, idVendor=0bda, idProduct=2838
usb 3-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
usb 3-5: Product: RTL2838UHIDIR
usb 3-5: Manufacturer: Realtek
usb 3-5: SerialNumber: 00000001
usb 3-5: dvb_usb_v2: found a 'Realtek RTL2832U reference design' in warm state
usb 3-5: dvb_usb_v2: will pass the complete MPEG2 transport stream to the software demuxer
DVB: registering new adapter (Realtek RTL2832U reference design)
usb 3-5: DVB: registering adapter 0 frontend 0 (Realtek RTL2832 (DVB-T))...
r820t 12-001a: creating new instance
r820t 12-001a: Rafael Micro r820t successfully identified
Registered IR keymap rc-empty
input: Realtek RTL2832U reference design as /devices/pci0000:00/0000:00:14.4/0000:02:05.2/usb3/3-5/rc/rc1/input17
rc1: Realtek RTL2832U reference design as /devices/pci0000:00/0000:00:14.4/0000:02:05.2/usb3/3-5/rc/rc1
input: MCE IR Keyboard/Mouse (dvb_usb_rtl28xxu) as /devices/virtual/input/input18
rc rc1: lirc_dev: driver ir-lirc-codec (dvb_usb_rtl28xxu) registered at minor = 0
usb 3-5: dvb_usb_v2: schedule remote query interval to 400 msecs
usb 3-5: dvb_usb_v2: 'Realtek RTL2832U reference design' successfully initialized and connected
```

```
lsusb -l output:
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0bda:2838 Realtek Semiconductor Corp. RTL2838 DVB-T
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 058f:6377 Alcor Micro Corp. Multimedia Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 005: ID 10d5:55a2 Uni Class Technology Co., Ltd 2Port KVMSwitcher
Bus 004 Device 004: ID 046d:c064 Logitech, Inc. 
Bus 004 Device 006: ID 413c:2010 Dell Computer Corp. Keyboard
Bus 004 Device 003: ID 413c:1003 Dell Computer Corp. Keyboard Hub
Bus 004 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

Thanks in advance!

---

### Post by howefield on 2015-08-23
Thread moved to the "*MINT*" forum.

---

