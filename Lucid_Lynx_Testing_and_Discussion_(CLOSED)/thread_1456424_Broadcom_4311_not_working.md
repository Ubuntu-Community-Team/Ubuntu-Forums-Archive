---
title: "Broadcom 4311 not working"
date: 2010-04-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ggffnn on 2010-04-17
I have a compaq presario v6000.
i tried everything...
install, reinstall, a lot of times bcmwl-kernel-source but i can't get my broadcom 4311 working (and i can't see broadcom drivers in system-administration-hwdrivers.
I get a randomic behaviour... sometimes it works, sometimes not. without any upgrade or system change.
in 9.04 everything was ok until i tried to install the new nvidia grforce6150 driver...

please help .....

ThankYou!!!!!

---

### Post by themagicmanfromtrent on 2010-04-17
Make sure your computer is connected to the internet via an ethernet cable.

Type **sudo apt-get install b43-fwcutter** into terminal.

Reboot your computer.

Browse to System > Administration > Hardware Drivers.

There should be an entry for your card. Enable it if it's not already enabled.

---

### Post by ggffnn on 2010-04-17
i've done it but nothing happened.
no broadcom driver in hardware drivers.
is there a startup log that i can post where i can find errors/warnings?
Thanks

---

### Post by ggffnn on 2010-04-17
one more thing... i've tried to reinstall lucid several times but i have my "Home" in a separate partition.
Maybe i have to delete completely my home partition too...:(

---

### Post by ggffnn on 2010-04-17
here are the result of lspci command:

spci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce Go 6150] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control



Please help:(

---

### Post by nanog on 2010-04-17
> sudo apt-get install b43-fwcutter
Bad advice IMO. The open source driver is no longer the default driver for many cards in ubuntu.

4311 is supported by the STA driver which was packaged by ubuntu using firmware provided by broadcom.

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

You can install this as follows:

```
sudo apt-get install bcmwl-kernel-source
```

You need to have DKMS installed. (sudo apt-get installed dkms)

This should have appeared automatically in Jockey so you should file a bug.

---

### Post by ggffnn on 2010-04-18
i've solved... how?
i reinstalled 8.04, then 8.10 and then... 9.04.
now in 9.04 everythin gis working fine.
i'll wait 1 month to install lucid.
thanks everybody anyway.

---

