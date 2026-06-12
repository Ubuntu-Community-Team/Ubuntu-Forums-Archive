---
title: "USB Installer not working, get error [??? ???]"
date: 2013-12-21
forum: Installation &amp; Upgrades
---

### Post by aluhvihn on 2013-12-21
So I have installed lubuntu on two of my laptops and they did wonders for them, so I decided to dig out my old laptop from '05 and breathe life back into it. When I tried to install lubuntu onto it through a LiveUSB though (same one I installed on both of my previous two), I get an error I don't know how to search up.

The installer's desktop mode on the laptop works fine, but when I try to run the actual installer, it goes through everything then after I choose to install with updates, I get the attached error. When I try to close the error window or press "OK", it just pops back up, and I can't shut off the installer, has anyone ever encountered this before?

Hardware info:
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
02:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
02:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
02:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
02:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection (rev 05)

---

### Post by buzzingrobot on 2013-12-21
What happens if you don't select the update while installing and download third-party software options?  Both those can be done after a successful install.

---

### Post by aluhvihn on 2013-12-21
Haha, awesome! That's what I did my very first time but it froze, this time I tried again and it worked! Thanks man. Is there any package or list of the third party applications that come with lubuntu that I can download to install?

---

### Post by ajgreeny on 2013-12-21
Just install the **lubuntu-restricted-extras** package and you'll get just about all you are likely to need.  And update the whole system as well, of course.

---

### Post by aluhvihn on 2013-12-21
Thank you all very much, these forums are speedy! wonderful community

---

