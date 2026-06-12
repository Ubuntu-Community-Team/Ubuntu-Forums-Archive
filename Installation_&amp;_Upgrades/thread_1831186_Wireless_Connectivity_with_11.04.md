---
title: "Wireless Connectivity with 11.04"
date: 2011-08-23
forum: Installation &amp; Upgrades
---

### Post by Herman Munster on 2011-08-23
I have 10.04 LTS installed on my HP nc6220 laptop and everything works beautifully. No other OS installed.
 
I recently downloaded 11.04 and created a bootable USB stick through 10.04. I booted from the USB and tried 11.04 instead of installing it. All worked except the wireless connection. It keeps trying to connect and eventually a window appears asking me for my wireless password. I enter the correct password and the same thing happens. I edited the network connection and made triple sure the password is correct, but still doesn't connect. I booted back into 10.04 and wrote down all the networking information. I then booted back into 11.04 and made sure everything matched, to no avail.
 
What am I missing? I like the look and feel of 11.04 and would like to use it.

---

### Post by mikewhatever on 2011-08-23
The only thing missing is the output of **lspci**, it would show the wireless hardware.

---

### Post by Herman Munster on 2011-08-23
> Ethernet controller:  Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 11)

I was able to connect to an unsecure wireless network that I know has internet connectivity.  Although I was able to connect to the wireless network, I was unable to access the internet.  When I checked the wireless properties, it showed the same configuration I have under 10.04 LTS.

Once again, when I tried to connect to my wireless network it doesn't recognize the password.

---

### Post by mikewhatever on 2011-08-23
> **Herman Munster said:**
> 
> Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 11) 
I was able to connect to an unsecure wireless network that I know has internet connectivity.  Although I was able to connect to the wireless network, I was unable to access the internet.  When I checked the wireless properties, it showed the same configuration I have under 10.04 LTS.

Once again, when I tried to connect to my wireless network it doesn't recognize the password.

Once again, you need to provide info on the wireless hardware. What you posted above is the network card (wired connection) and seems to be irrelevant.

---

### Post by Herman Munster on 2011-08-23
My apologies for the screwup.

```
02:04.0 Network Controller:  Intel Corporation PRO/Wireless 220BG (Calexico2) Network Connection (rev 05)
```

The exact same thing shows up under both versions.

---

### Post by Herman Munster on 2011-08-23
To be more specific, if it helps.

```
02:04.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:12f5]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (750ns min, 6000ns max), Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 21
    Region 0: Memory at d0400000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [dc] Power Management version 2
        Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=1 PME-
    Kernel driver in use: ipw2200
    Kernel modules: ipw2200
```

---

### Post by WarrenSH on 2011-08-23
Seeking more info on this as well I just upgraded 11.04 love it but no WiFi for me :( 

```
Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139-
```

---

### Post by Herman Munster on 2011-08-25
Any ideas out there, or shall I wait for the LTS version?

---

### Post by Herman Munster on 2011-09-09
Can anyone provide some insight or solution for this problem?

---

### Post by cutekazuya on 2011-09-09
hi mate,

try to disable power saving for wifi and pci. In terminal >
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]```
sudo touch /etc/pm/power.d/wireless
sudo touch /etc/pm/power.d/pcie_aspm
```

Or alternatively, try installing "wicd" and see if that connects. Also try to change from WPA2 to WPA or WEP and see if that is the problem.

---

### Post by Herman Munster on 2011-09-09
> **cutekazuya said:**
> hi mate,

try to disable power saving for wifi and pci. In terminal >
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]```
sudo touch /etc/pm/power.d/wireless
sudo touch /etc/pm/power.d/pcie_aspm
```Or alternatively, try installing "wicd" and see if that connects. Also try to change from WPA2 to WPA or WEP and see if that is the problem.

Thanks.  Tried it out and still no connectivity for wireless.

It's frustrating when it works on one version but not another.

---

### Post by Herman Munster on 2011-09-17
Update:

I upgraded 10.04LTS to 10.10 and everything worked.  I subsequently upgraded 10.10 to 11.04 and all is in working order.

Obviously, there is a wireless bug in 11.04 on a clean install.

---

