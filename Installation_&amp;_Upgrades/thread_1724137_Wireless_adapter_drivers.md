---
title: "Wireless adapter drivers"
date: 2011-04-07
forum: Installation &amp; Upgrades
---

### Post by &lt;insert clever username&gt; on 2011-04-07
Hey guys, recently (today) installed ubuntu 10.10. everything went fine but it says my wireless firmware is not supported. I am assuming this means the drivers are not installed.
I am running a Dell inspiron 1420. the wireless device is a broadcom 802.11g wireless adapter. I would love some assistance.

Cheers,
Evan

EDIT: problem solved. Thank you

---

### Post by Quackers on 2011-04-07
Can you connect to a router using an ethernet cable? If so, run System > Admin > Additional Drivers (if it doesn't run automatically) and see if drivers for the wireless are found.

---

### Post by &lt;insert clever username&gt; on 2011-04-08
connected via Ethernet cable and no drivers were found. perhaps my wireless adapter Isn't compatible? I know my old laptop never had any problems with it's wireless adapter.

---

### Post by M4570D0N on 2011-04-08
What you you get when you type this in the terminal:
```
sudo lspci -vnn
```and locate the device(s) related to your hardware?

example, from my laptop:

```
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection [8086:4237]
    Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1211]
    Flags: bus master, fast devsel, latency 0, IRQ 49
    Memory at db600000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [c8] Power Management version 3
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [e0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number
    Kernel driver in use: iwlagn
    Kernel modules: iwlagn

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:3602]
    Flags: bus master, fast devsel, latency 0, IRQ 46
    I/O ports at 6000 [size=256]
    Memory at d1410000 (64-bit, prefetchable) [size=4K]
    Memory at d1400000 (64-bit, prefetchable) [size=64K]
    Expansion ROM at d1420000 [disabled] [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [ac] MSI-X: Enable- Count=2 Masked-
    Capabilities: [cc] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number
    Kernel driver in use: r8169
    Kernel modules: r8169

```

---

### Post by &lt;insert clever username&gt; on 2011-04-08
I solved my problem. When I was updating it found new drivers like in the first response. Thank you for your help.

---

