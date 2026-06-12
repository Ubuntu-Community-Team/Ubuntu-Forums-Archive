---
title: "slow since 9.10"
date: 2009-12-31
forum: Installation &amp; Upgrades
---

### Post by rudedcam on 2009-12-31
Dell inspiron 1420

ever since the update to 9.10, the OS is very slow. i think it might have something to do with the graphic drivers.

i have installed Envyng but unfortunately no driver seemed to be compatible.
[[IMG]http://imgur.com/WTkp3s.png[/IMG]](http://imgur.com/WTkp3.jpg)
the question is: how do i find the right driver?
```
sudo lspci
[sudo] password for °°°°°°: 
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 [COLOR="Red"]VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)[/COLOR]
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

```

---

### Post by Revolutionary101 on 2009-12-31
A quick way to test if your graphics drivers are working is to turn on extra visual effects. To turn the effects on go to System>Preferences>Appearance then go to the Visual Effects tab. If you can't turn on the extra or even the normal visual effects then your graphics driver is not installed or not working.

---

### Post by rudedcam on 2009-12-31
> **Revolutionary101 said:**
> A quick way to test if your graphics drivers are working is to turn on extra visual effects. To turn the effects on go to System>Preferences>Appearance then go to the Visual Effects tab. If you can't turn on the extra or even the normal visual effects then your graphics driver is not installed or not working.

yup, it tells me the "desktop effects could not be enabled". 

do you know what to do from there?

happy new years

---

### Post by Revolutionary101 on 2009-12-31
You should be able to download the graphics driver from this website. [http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=13815&lang=eng]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=13815&lang=eng")

Also you could try to go to System>Administration>Hardware Drivers. This will search your computer and see if there are any drivers that need to be installed. 

and Happy New Years to you too!

---

### Post by rudedcam on 2009-12-31
sorry mate, System>Administration>Hardware Drivers gives me no options,
[IMG]http://imgur.com/g4Hhq.jpg[/IMG]

"http://downloadcenter.intel.com/Deta...13815&lang=eng" gives me a somewhat list of drivers, but none of them clearly stand out of the others for possible use.

i have myself a dell inspiron 1545 and i freshly installed 9.10 today. I experience the same lame experience as on my father's (inspiron 1420). same problems and all. looking around for answers is frustration due to the slowness. 
i myself will go back to 9.4, my father will go back to a single windows OS. so it it solved

thanks for your help

---

