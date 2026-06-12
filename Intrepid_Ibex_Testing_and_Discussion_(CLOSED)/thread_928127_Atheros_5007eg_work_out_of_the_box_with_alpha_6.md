---
title: "Atheros 5007eg work out of the box with alpha 6?"
date: 2008-09-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by 67GTA on 2008-09-23
I have been waiting to see if the new madwifi patch for ar5007eg will make it into 8.10. Alpha 5 didn't work. Can anyone tell me if alpha 6 works with ar5007eg without using ndiswrapper before I download the ISO?

---

### Post by canga on 2008-09-25
From dmesg following today's 2.27.4 kernel upgrade
```
 ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
```
and so I am now able to use wlan for network connection from my Aspire One using the ath5k driver.

Google tells me that ar2425 chipset is in ar5007eg, so yes it works.

---

### Post by Perpetual on 2008-09-25
That's good to hear.  Too bad I can't get 8.10 Alphas to boot on my laptop!  Frustrated.

---

### Post by 67GTA on 2008-09-25
Awesome! Thanks.

---

### Post by tim183 on 2008-09-25
my ar5007eg is getting "closer" to working but still fails me.

I can see the available networks, but when I attempt to connect (both secure and unsecure) it fails...

this is soooo frustrating, im thinking I could pull my new laptop apart and put a compatible wireless card in there.... thoughts?

---

### Post by mckooiker on 2008-10-18
> **canga said:**
> From dmesg following today's 2.27.4 kernel upgrade
```
 ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
```
and so I am now able to use wlan for network connection from my Aspire One using the ath5k driver.

Google tells me that ar2425 chipset is in ar5007eg, so yes it works.
Not true for me :(
I just installed and upgraded the latest kubuntu (8.10), blacklisted ath_pci, rebooted:
dmesg |grep ath: 
ath5k_pci 0000:08:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
ath5k_pci 0000:08:00.0: setting latency timer to 64
ath5k_pci 0000:08:00.0: registered as 'phy0'
ath5k phy0: Support for RF2425 is under development.
ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)

iwlist wlan0 scan:
wlan0     No scan results

lspci -vv:
08:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 04)
        Subsystem: Atheros Communications Inc. Device 3067
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 18
        Region 0: Memory at fa000000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath5k_pci
        Kernel modules: ath5k, ath_pci

I must say that I did not even manage to get the wireless working with madwifi, ticket 1192 (?), ndiswrapper etc. It only works under windows (vista).
I have a Fujitsu Siemens Amilo Li 2732

I hope someone can help me!

---

### Post by mckooiker on 2008-10-19
I managed to get the Atheros AR5007EG working. I'll try to summarize the steps I performed to get it working, hoping it will be usefull to someone else:

Laptop: Fujitsu-Siemens Amilo Li 2732 (activation of wireless = Fn+F1).
Operating System: Kubuntu 8.10 beta (containing kernel 2.6.27.7-generic)
Atheros AR242x wirlesss adapter

Ok, first thing I did was to add "[COLOR="Red"]blacklist ath_pci[/COLOR]" in "[COLOR="Red"]/etc/modprobe.d/blacklist[/COLOR]"
then add "[COLOR="Red"]acerhk[/COLOR]" to "[COLOR="Red"]/etc/modules[/COLOR]" (http://ubuntuforums.org/showthread.php?t=644899)---> No need to download/compile/install the acerhk module,it's already there!!

then you need to make the file "[COLOR="Red"]amilo_special_keys.modprobe[/COLOR]" and put it in the folder: "[COLOR="Red"]/etc/modprobe.d/[/COLOR]" The file should contain the following text:
[COLOR="Red"][I]# set up kernel module acerhk to enable Fujitsu Siemens Amilo Li1718 special keys
# and enable wireless when the module is inserted.
# NOTE: to have the wireless hardware disabled until you press the wireless key on the laptop,
# simply replace "echo 1" with "echo 0" in the command below. 

install acerhk /sbin/modprobe --ignore-install acerhk force_series=6805 autowlan=1; echo 1 > /proc/driver/acerhk/wirelessled[/I][/COLOR]

One more thing to do: edit your "[COLOR="Red"]/etc/network/interfaces[/COLOR]" file.
It should contain the right information to be able to connect to your router. This may change, depending on encryption, static IP vs. dhcp etc.
I added the following lines:

[COLOR="Red"]auto wlan0
iface wlan0 inet dhcp
wireless-essid xxxxxxxxx
wireless-mode Managed
wireless-key [1] xxxxxxxxxxxxxxxxxx[/COLOR]

Reboot the computer.
The wireless led should be turned on after boot.
iwlist scan should result in the detection of the wireless networks around you.
If you do not manage to get your wireless working, please respond to this message, maybe I can help.....

Some problems: the KNetwork manager does not see the wireless networks (Probably because I don't know how to configure it, since I always used gnome).
The Led is always turned on and I don't manage to switch the wireless off.

---

### Post by mckooiker on 2008-10-20
P.S.: Today I started my computer and I was not able to connect/see wireless connections. After the following commands I was back on-line:

[COLOR="Red"]ifconfig wlan0 down

ifconfig wlan0 up

/etc/init.d/networking restart[/COLOR]

Edit:
with newer versions of ubuntu this wireless card is supported (I think from 9.04). Try:
**[COLOR="Red"]sudo modprobe acer_wmi[/COLOR]**
Wireless led should turn on instantly.
check: [http://www.vleeuwen.net/2009/06/wireless-fix-on-amilo-running-ubuntu](http://www.vleeuwen.net/2009/06/wireless-fix-on-amilo-running-ubuntu)

---

