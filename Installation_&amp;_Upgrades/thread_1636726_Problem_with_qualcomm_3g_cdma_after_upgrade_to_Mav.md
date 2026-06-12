---
title: "Problem with qualcomm 3g cdma after upgrade to Maveric"
date: 2010-12-03
forum: Installation &amp; Upgrades
---

### Post by connyh on 2010-12-03
Hi,
I upgraded to Maverick Meerkat and now I have huge problems wit my 3g connection
I use a qualcomm 3g cdma (pcmia board) and everyting looks ok when i check with lsusb I get:
Bus 009 Device 002: ID 05c6:1000 Qualcomm, Inc. Mass Storage Device
and then i tried sudo modeprobe option and got:
hub 9-0:1.0: USB hub found
Laptop kernel: [ 9358.342326] hub 9-0:1.0: 1 port detected
Laptop kernel: [ 9361.400167] usb 9-1: new full speed USB device using ohci_hcd and address 2
Laptop kernel: [ 9361.626255] scsi8 : usb-storage 9-1:1.0
Laptop kernel: [ 9362.632820] scsi 8:0:0:0: CD-ROM            GT       HSDPA Modem      3.00 PQ: 0 ANSI: 2
Laptop kernel: [ 9362.685762] sr0: scsi-1 drive
Laptop kernel: [ 9362.687461] sr 8:0:0:0: Attached scsi generic sg2 type 5

Then I tried sudo modprobe cdc-acm with following result:

Laptop kernel: [ 9622.785357] usbcore: registered new interface driver cdc_acm
Laptop kernel: [ 9622.785360] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
From my point of view this is ok and the modem should appear in the NetworkManager but NO. 
Is there someone out there that have a solution to my problem or can point me in the right direction?
As for now I can't see any Mobile Brodband connect in my Network Manager, the setup works and I can select my
provider but nothing shows up in Network Manage. *There is [I]no connection* available, *hence* no internet[/I]
M

---

