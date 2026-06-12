---
title: "Help - was working now - Aspire one lost network"
date: 2009-03-24
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Peter09 on 2009-03-24
After an update yesterday I have lost my wireless connection for my Aspire One. It has been working simply by blacklisting acer_wmi, however I now get

> peter@aspirepc:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:96:12:2a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.0.16 latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 46:26:8a:0c:eb:bd
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


and this shows no driver attached.... any one any ideas on this?


Note: I have also lost the wireless connection on my Toshiba Satellite at the same time - Its showing the network but will not connect.

---

### Post by Peter09 on 2009-03-24
Found this in dmesg

> [  450.312694] ath5k_pci 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[  450.312724] ath5k_pci 0000:03:00.0: setting latency timer to 64
[  450.312909] ath5k_pci 0000:03:00.0: registered as 'phy0'
[  450.322994] ath5k phy0: failed to wakeup the MAC Chip
[  450.323068] ath5k_pci 0000:03:00.0: PCI INT A disabled
[  450.325244] ath5k_pci: probe of 0000:03:00.0 failed with error -5


---

### Post by taavikko on 2009-03-24
> **Peter09 said:**
> Found this in dmesg

Please shutdown PC completely, then restart. that should fix the 
wakeup issue.

---

### Post by Peter09 on 2009-03-24
No - tried that - this is something that started yesterday, after an update - just do not know what changed.

---

### Post by Peter09 on 2009-03-24
Well I got this working in the end by doing -

```
sudo modprobe ath5k
```

Why the driver was missing to start with I have no idea :(

---

### Post by Peter09 on 2009-03-25
I have two laptops (an Aspire one and a Toshiba) they both use the ath5k wireless driver. Over the last couple of days I have found on both machines that the ath5k driver is not being loaded automatically at boot. I have to do

```
sudo modprobe ath5k
```
to get the wireless up. Any one know what is happening?

---

### Post by macroshaft on 2009-03-25
I suspect modprobe ath5k 'should' work for me as I have an atheros AR5006EG but it tells me the module cannot be found. Any ideas?

For those of you stuck modprobing to stay online goto a terminal, type 

sudo gedit /etc/modules 

and then add the line 

ath5k

save, fixed!

---

