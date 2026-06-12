---
title: "how to recover deleted printer?"
date: 2008-10-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by lime4x4 on 2008-10-17
I accidently deleted the printer now i have no printer and it won't re-detect it. It's a usb canon printer

---

### Post by racmar on 2008-10-18
Have you tried:

```
System -> Administration -> Printing -> New printer?
```

Also, try looking in the View menu from the same Printing window.

---

### Post by MaX on 2008-10-18
You can always try to disconnect the printer and connect it again, this usually triggers the hardware detection.

---

### Post by lime4x4 on 2008-10-18
i've tried both of those suggestions and it still won't show up

---

### Post by philinux on 2008-10-18
Surely when you go add new printer the list of canons should contain yours.

---

### Post by lime4x4 on 2008-10-18
it contains nothing

---

### Post by philinux on 2008-10-18
> **lime4x4 said:**
> it contains nothing

Odd indeed. Give the blighter a reboot. Then plug your printer in.

---

### Post by racmar on 2008-10-18
How about the obvious... Most printers have to be powered "ON" to be detected.

Also, try this command and post the output ( if it changes ) after unplugging and replugging your printer.
```
watch "dmesg | tail -30"
```

---

### Post by lime4x4 on 2008-10-18
nope doesn't change


watch "dmesg | tail -30"

[   82.446361] usb 1-3.1: configuration #1 chosen from 1 choice
[   82.526020] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   82.526734] usbcore: registered new interface driver btusb
[   86.248268] eth0: no link during initialization.
[   86.249337] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   86.643050] NET: Registered protocol family 17
[   94.005910] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[   94.006845] input: Logitech MX5000 Keyboard as /devices/pci0000:00/0000:00:0b
.0/usb1/1-3/1-3.1/1-3.1:1.0/bluetooth/hci0/hci0:11/input8
[   96.340012] eth1: no IPv6 routers present
[  178.361907] type=1503 audit(1224336719.856:5): operation="inode_permission" r
equested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6386/net/" pid=6386 pr
ofile="/usr/sbin/cupsd"
[  179.541589] type=1503 audit(1224336721.036:6): operation="inode_permission" r
equested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6393/net/" pid=6393 pr
ofile="/usr/sbin/cupsd"
[  179.541636] type=1503 audit(1224336721.036:7): operation="socket_create" fami
ly="ax25" sock_type="dgram" protocol=0 pid=6393 profile="/usr/sbin/cupsd"
[  179.541643] type=1503 audit(1224336721.036:8): operation="socket_create" fami
ly="netrom" sock_type="seqpacket" protocol=0 pid=6393 profile="/usr/sbin/cupsd"
[  179.541658] type=1503 audit(1224336721.036:9): operation="socket_create" fami
ly="rose" sock_type="dgram" protocol=0 pid=6393 profile="/usr/sbin/cupsd"

---

### Post by inportb on 2008-10-18
Type *lsusb* to see if your printer is detected at all. I get a line for my USB printer:

> Bus 005 Device 003: ID 03f0:7504 Hewlett-Packard Printing Support

---

### Post by racmar on 2008-10-18
Since dmesg doesn't change, I'm guessing either your printer is off, or you've pulled the usb plug out from it.  Please double check all connections, and remove power from your printer.  Then connect everything back and either use lsusb or dmesg to determine if anything has been recognized.  Also, try a different usb port on your computer.

---

