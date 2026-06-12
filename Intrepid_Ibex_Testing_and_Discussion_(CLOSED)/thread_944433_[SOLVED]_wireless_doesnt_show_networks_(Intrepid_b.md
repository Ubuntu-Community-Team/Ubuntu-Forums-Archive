---
title: "[SOLVED] wireless doesnt show networks (Intrepid beta)"
date: 2008-10-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by heartwarmer on 2008-10-11
Hello..

I recently installed ubuntu Intrepid 8.10 beta (clean installation),everything worked ok, except wireless, it doesn't show available networks although wireless is on and and the led is on

iwlist scan:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

lshw:
*-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wmaster0
                version: 02
                serial: 00:18:de:c1:0a:81
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11bg

Thanks in advance.

---

### Post by xfalcon on 2008-10-11
I am also a beginner but I have similar problem like you do. I installed xubuntu yesterday. I have both an ethernet card (PCI) and a wireless card (PCI) installed in my computer. my computer didn't recognised the wireless card but recognised the ethernet card. So I looked at some forum:

[http://ubuntuforums.org/archive/index.php/t-825187.html](http://ubuntuforums.org/archive/index.php/t-825187.html)

Last night, I just removed the ethernet card and put the wireless card in the PCI slot (of the ethernet card), I didn't put the ethernet card back. After I start the computer, the wireless card is now recognised and working.

My suggestion, maybe you can just pull the wireless card and put it back on the same PCI slot of another slot... It's worth a try.. Good luck..

---

### Post by heartwarmer on 2008-10-11
thanks  xfalcon for reply, well i cant do what you did because its
a laptop, what i did is i uninstalled network manager and installed
wicd,got the same results,uninstalled wicd and reinstalled network
manager,it started to see the networks,so i could see my home network,but
i still cant connect to it

---

### Post by heartwarmer on 2008-10-11
OMG, it just worked, i did a restart and it worked.

---

