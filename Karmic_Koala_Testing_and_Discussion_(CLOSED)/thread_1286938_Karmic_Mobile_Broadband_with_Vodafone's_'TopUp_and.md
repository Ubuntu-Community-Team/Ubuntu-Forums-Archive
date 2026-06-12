---
title: "Karmic Mobile Broadband with Vodafone's 'TopUp and Go' USB dongle"
date: 2009-10-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Muflon on 2009-10-09
Yesterday I purchased a Vodafone 'TopUp and Go' USB dongle.  This is my experience with Karmic Beta.

After booting into Karmic I plugged the device in and waited for the light on the dongle turned blue.

```
lsusb
Bus 002 Device 003: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem

```

After installing the device using Network Manager

```
route

Kernel IP routing table

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

10.64.64.64     *               255.255.255.255 UH    0      0        0 ppp0

default         10.64.64.64     0.0.0.0         UG    0      0        0 ppp0


```

```
tracepath 10.64.64.64

 1:  10.xx.xx.132 (10.xx.xx.132)                            0.194ms pmtu 1500

 1:  no reply

 2:  no reply

 3:  no reply

```

It looks like it should be working but its not :(

Sorry about all the screen shots but I got a bit carried away!

Muflon

---

### Post by Muflon on 2009-10-10
More info

```
[ 1965.608183] usb 2-4: new high speed USB device using ehci_hcd and address 8
[ 1965.751660] usb 2-4: configuration #1 chosen from 1 choice
[ 1965.757793] scsi20 : SCSI emulation for USB Mass Storage devices
[ 1965.757991] usb-storage: device found at 8
[ 1965.757993] usb-storage: waiting for device to settle before scanning
[ 1965.758549] usb 2-4: USB disconnect, address 8
[ 1973.328284] usb 2-4: new high speed USB device using ehci_hcd and address 9
[ 1973.473264] usb 2-4: configuration #1 chosen from 1 choice
[ 1973.477815] option 2-4:1.0: GSM modem (1-port) converter detected
[ 1973.477977] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB0
[ 1973.478177] option 2-4:1.1: GSM modem (1-port) converter detected
[ 1973.478273] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB1
[ 1973.501592] scsi23 : SCSI emulation for USB Mass Storage devices
[ 1973.503719] usb-storage: device found at 9
[ 1973.503722] usb-storage: waiting for device to settle before scanning
[ 1973.503839] scsi24 : SCSI emulation for USB Mass Storage devices
[ 1973.511043] usb-storage: device found at 9
[ 1973.511046] usb-storage: waiting for device to settle before scanning
[ 1978.507230] usb-storage: device scan complete
[ 1978.509257] scsi 23:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[ 1978.516340] usb-storage: device scan complete
[ 1978.518701] scsi 24:0:0:0: Direct-Access     HUAWEI   MMC Storage      2.31 PQ: 0 ANSI: 2
[ 1978.537770] sr1: scsi-1 drive
[ 1978.537993] sr 23:0:0:0: Attached scsi CD-ROM sr1
[ 1978.538125] sr 23:0:0:0: Attached scsi generic sg2 type 5
[ 1978.538476] sd 24:0:0:0: Attached scsi generic sg3 type 0
[ 1978.553213] sd 24:0:0:0: [sdb] Attached SCSI removable disk
[ 1992.811897] ISO 9660 Extensions: Microsoft Joliet Level 1
[ 1992.816886] ISOFS: changing to secondary root

```

---

### Post by terry_gardener on 2009-10-10
i had similar problem with the t-mobile 530 with jaunty unr.

i had to use vodafone mobile connect 

[http://www.betavine.net/bvportal/resources/datacards/os/ubuntu]("http://www.betavine.net/bvportal/resources/datacards/os/ubuntu")

i also had to replace gnome-network manager with wicd

---

### Post by Muflon on 2009-10-10
My USB dongle is now working :)

In the end I put the dongle into a Windows machine and registered it online so that I could check the usage online.  I then plugged it back into my Karmic laptop and it works.  I am writing this post using the Vodafone dongle.

Essentially after registering the dongle using Windows it works in Karmic out of the box with no special packages or settings. :KS

Muflon

---

