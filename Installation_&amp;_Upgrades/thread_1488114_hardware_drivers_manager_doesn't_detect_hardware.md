---
title: "hardware drivers manager doesn't detect hardware"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by zenek89 on 2010-05-19
I have a problem with "**hardware drivers**" manager. When I'm running **Live CD** on my computer, **driver's manager** **is able to detect** my wireless broadcom chipset and other two of my devices. It **runs** the drivers and I'm able to use my **broadcom** while using **liveCD**. But **after** I installed fresh Ubuntu 9.10 it** doesn't detec**t any of these three and it says [B]"no proprietary drivers are in use on this system"
[/B]

When I simply use command ```
lspci -nn
```it shows all of them:
```
[10de:055f] (rev a2)
00:04.0 USB Controller [0c03]: nVidia Corporation MCP67 OHCI USB 1.1 Controller
[10de:055e] (rev a2)
00:04.1 USB Controller [0c03]: nVidia Corporation MCP67 EHCI USB 2.0 Controller 
[10de:055f] (rev a2)
00:06.0 IDE interface [0101]: nVidia Corporation MCP67 IDE Controller 
[10de:0560] (rev a1)
[B]00:07.0 Audio device [0403]: nVidia Corporation MCP67 High Definition Audio 
[10de:055c] (rev a1)[/B]
00:08.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Bridge 
[10de:0561] (rev a2)
00:09.0 IDE interface [0101]: nVidia Corporation MCP67 AHCI Controller 
[10de:0550] (rev a2)
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP67 Ethernet 
[10de:054c] (rev a2)
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Express Bridge 
[10de:0563] (rev a2)
00:0d.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Express Bridge 
[10de:0563] (rev a2)
**00:12.0 VGA compatible controller [0300]: nVidia Corporation C67 [GeForce 7150M / nForce 630M] **
[10de:0531] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
[1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map 
[1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller 
[1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control 
[1022:1103]
02:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller 
[1180:0832] (rev 05)
02:05.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter 
[1180:0822] (rev 22)
02:05.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller 
[1180:0843] (rev 12)
02:05.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter 
[1180:0592] (rev 12)
02:05.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller 
[1180:0852] (rev ff)
03:00.0 **Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)**
 
 
```I've checked **synaptic package manager** and one file called **"bcmwl-_something_" **was installed already during the system installation. *(info about this file says that this file is responsible for detecting broadcom's chips on PC)*

---

### Post by chili555 on 2010-05-19
the module bcmwl-kernel-source provides the driver wl which drives your device; viz:```
$ modinfo wl | grep 4328
alias:          pci:v0000[COLOR="Blue"]14E4[/COLOR]d0000[COLOR="Blue"]4328[/COLOR]sv*sd*bc*sc*i*
```Is the module loaded?```
lsmod | grep wl
```If it is, it ought to have created a wireless interface, wlan0, perhaps:```
iwconfig
```If you have it, you ought to be able to click the Network Manager icon and connect.

If not, load it:```
sudo modprobe wl
```Let's troubleshoot:```
dmesg | grep wl
```

---

### Post by zenek89 on 2010-05-19
```


zenek@zenek-laptop:~$  modinfo wl | grep 4328
ERROR: modinfo: could not find module wl


``````

zenek@zenek-laptop:~$ iwconfig
lo  
no wireless extensions.

eth0  
no wireless extensions.

``````


zenek@zenek-laptop:~$ sudo modprobe wl
[sudo] password for zenek:
FATAL: Module wl not found


```**after this**:
```

dmesg | grep wl

```**nothing showed**

---

### Post by zenek89 on 2010-05-19
I suggest that drivers just are not installed, and I need more help on "drivers manager". Why does it detect hardware using LiveCD, but after installation it just looses it.

---

### Post by chili555 on 2010-05-19
Open up System > Administration > Synaptic and select Settings > Repositories and add the install CD as a source. Press Reload and search for bcmwl-kernel-source and install it. Then reboot and see if all is well.

---

### Post by zenek89 on 2010-05-20
thank You chili it worked for me !!

---

