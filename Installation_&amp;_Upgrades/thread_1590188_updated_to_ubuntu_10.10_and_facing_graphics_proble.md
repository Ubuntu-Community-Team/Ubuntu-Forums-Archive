---
title: "updated to ubuntu 10.10 and facing graphics problem"
date: 2010-10-07
forum: Installation &amp; Upgrades
---

### Post by gudurukarthik on 2010-10-07
hey , cheers for the new ubuntu 10.10
hey i have some problem ,when i try to activate the graphics driver , it is not getting to activated it says 
"""
Sorry, the installation of this driver failed.

Please have a look at the log file for details.: /var/log/jockey.log
                                                                                                       """"
hey can u please help me . as im new to ubuntu i whould be thankfull if u can give me some clear information on how to solve this problem

---

### Post by andrewthomas on 2010-10-07
post the output of 

```
cat /var/log/jockey.log
```

in the terminal.

---

### Post by gudurukarthik on 2010-10-07
hey
i tryed doing waht u said but the same thing comes when ever i try activate grafics( in my sony centrino2 ,6gb fw series laptop ).
do u konow what else can be done ? and hey in youtube if i try to fulscreen it it is crasing down which makes me refresh and watch in that small part .

---

### Post by efflandt on 2010-10-07
What graphic card/chip do you have (at least the line related to that from output of **lspci** in a terminal), and what graphics driver are you trying to install or activate?

For example in another thread someone was trying everything to get an **nvidia** driver working when lspci showed that he had **Intel** graphics.  But even if you are trying to install a graphics driver for the correct manufacturer, it is possible that older card/chips are no longer supported by that driver.

---

### Post by gudurukarthik on 2010-10-07
an d after lspci in terminal it says 
karthik@karthik-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M96 [Mobility Radeon HD 4650]
01:00.1 Audio device: ATI Technologies Inc RV710/730
06:00.0 Network controller: Intel Corporation WiFi Link 5100
08:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 14)
0a:03.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
0a:03.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0a:03.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)

---

