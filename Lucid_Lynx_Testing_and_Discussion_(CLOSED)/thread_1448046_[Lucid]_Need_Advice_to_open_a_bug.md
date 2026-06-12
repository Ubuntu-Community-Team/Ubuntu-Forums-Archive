---
title: "[Lucid] Need Advice to open a bug"
date: 2010-04-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by FrançoisB on 2010-04-06
Hi,

I encountered an issue with the Lucid beta 1 and I would like to open a new bug. I don't know how to retrieve the relevant information to help the developers.

Here is my draft : 

> There is lag on all my audio and video (Rythmbox, Totem...) every few seconds.
The problem disappears when I add "noapic" in the kernel parameters.
I didn't notice any error messages in the system log (syslog...)

lsb_release -rd
Description:    Ubuntu lucid (development branch)
Release:    10.04

lsusb:
:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 8800M GTX] (rev a2)
06:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
0c:07.0 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
0c:07.1 SD Host controller: ENE Technology Inc ENE PCI SmartMedia / xD Card Reader Controller
0c:07.3 FLASH memory: ENE Technology Inc ENE PCI Secure Digital / MMC Card Reader Controller
0c:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
I think it will be difficult to understand the issue because this report does not sound precise enough. But I don't know how to be more precise because I don't see any error logs. The only one relevant information I have is that "noapic" kernel parameter fixes the issue.

Any help will be appreciated, thanks in advance

---

### Post by overdrank on 2010-04-06
Hi and welcome, moved to Lucid Lynx Testing and Discussion :)

---

### Post by philinux on 2010-04-06
> **FrançoisB said:**
> Hi,

I encountered an issue with the Lucid beta 1 and I would like to open a new bug. I don't know how to retrieve the relevant information to help the developers.

Here is my draft : 

I think it will be difficult to understand the issue because this report does not sound precise enough. But I don't know how to be more precise because I don't see any error logs. The only one relevant information I have is that "noapic" kernel parameter fixes the issue.

Any help will be appreciated, thanks in advance

Open a terminal and use this.

```
ubuntu-bug linux
```

Add your lsusb output and any other relevant stuff to the bug report.

---

### Post by FrançoisB on 2010-04-06
Thanks for your help!

Edit : it is done : [https://bugs.launchpad.net/ubuntu/+bug/556727](https://bugs.launchpad.net/ubuntu/+bug/556727)
Thanks again

---

### Post by FrançoisB on 2010-04-08
One more question : What is the consequence to fix this problem by "noapic" in the kernel parameters? Everything looks ok but maybe there is a side effect?

---

### Post by ranch hand on 2010-04-08
Well things might well work better.

The thing to do is when the screen menu opens hit e.  This will let you edit the menu entry there.  The instruction string is on the "linux" line.

This will not change anything except that string for that boot only.  This way you can try it without any real side effects as if it is not good you need only reboot and things will be the same as they are now.

---

