---
title: "My problems after installing Ubuntu 10.4"
date: 2010-09-29
forum: Installation &amp; Upgrades
---

### Post by sabajamalian on 2010-09-29
I have recently installed Ubuntu 10.04 beside my Windows XP on my laptop:
Dell XPS 1330

I`m now facing some problems with my new OS : 

 1. The driver for my wireless network card isn't recognized although I have installed the recommended driver which was in Ubuntu Hardware Driver section.

 2. When I connect my laptop to my TV using HDMI port, the screen is OK but there is no sound!

 3. When by any reason my network cable is unplugged, the whole network service goes down and I have to restart the system.

Thanks in advance for your helps. 


lspci results: 

    00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
    00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)  
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
    00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)    
    00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)    
    01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GS] (rev a1)
    03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)   
    03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)    
    03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)    
    03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)    
    03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)   
    09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)    
    0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)           
    


    **** List of PLAYBACK Hardware Devices ****    
    card 0: Intel [HDA Intel], 
        device 0: STAC92xx Analog [STAC92xx Analog]
        Subdevices: 1/1
      Subdevice #0: subdevice #0
    
    card 0: Intel [HDA Intel], 
        device 1: STAC92xx Digital [STAC92xx Digital]
        Subdevices: 1/1
    
      Subdevice #0: subdevice #0



Thanks again for your time.

---

### Post by garvinrick4 on 2010-09-29
Click on sound applet in upper right hand corner to  Sound Preferences to Hardware to Profile there is choices of HDMI there. Dells drivers are proprietary from Dell if you got
them you got them if not you do not. Dell takes Windows apart and does not ship drivers
with them. They have their own so as to keep you dependent upon them. So they can smack you on the knuckles if you stray to far from them. Any which way does it recognize
your TV in monitors as the right size? If there select it. If does not work does it work in XP.
Large tv's in monitors are a pain in Linux it seems. Found drivers in Ubuntu for 32 inch Sony but not 40 inch.

---

