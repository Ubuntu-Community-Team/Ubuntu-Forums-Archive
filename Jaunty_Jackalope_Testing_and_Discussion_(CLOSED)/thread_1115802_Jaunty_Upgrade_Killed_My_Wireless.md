---
title: "Jaunty Upgrade Killed My Wireless"
date: 2009-04-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by moore.bryan on 2009-04-04
When I upgraded from Hardy to Intrepid, ath5k worked out of the box and solved all my wireless woes; now, they've returned. Upgrading to the Jaunty beta killed my wireless and after trying all the "tricks" in other posts, I'm stumped. Here's my info:

[LIST=1]
[*]Machine Brand/Model:```
Lenovo Thinkpad z61e
```
[*]Output of lspci:```
03:00.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)
```
[*]Output of ifconfig only shows eth0 and lo
[*]Output of iwconfig only shows lo, eth0, wmaster0, and wlan0.
[*]Output of lsmod | grep ath5k:```
ath5k 107008 0 / mac80211 217208 1 ath5k / led_class 12036 2 ath5k,thinkpad_acpi / cfg80211 38032 2 ath5k,mac80211
```
[*]Output of dmesg | grep ath5k:```
ath5k_pci 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 / ath5k_pci 0000:03:00.0: setting latency timer to 64 / ath5k_pci 0000:03:00.0: registered as "phy0" / Registered led device: ath5k-phy0::rx / Registered led device: ath5k-phy0::rx / ath5k phy0: Atheros AR5414 chip found (MAC: 0xa3, PHY: 0x61)
```
[*]Output for wireless with sudo lshw -C network:```
#-network DISABLED / description: Wireless interface / product: AR5212 802.11abg NIC / vendor: Atheros Communications Inc. / physical id: 0 / bus info: pci@0000:03:00.0 / logical name: wmaster0 / version: 01 / serial: 00:19:7e:25:8d:31 / width: 64 bits / clock: 33MHz / capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless / configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11abg
```
[*]Output of lsb_release -d: ```
Description: Ubuntu Jaunty (development branch)
```
[*]Output of uname -mr:```
2.6.28-11-generic i686
```
[/LIST]
Things I'm not sure about is: since when did ath0 turn to wmaster and why? In wicd, ath5k isn't even a choice for driver, when it was in Intrepid. Any help would be GREATLY appreciated; thanks guys and gals.

EDIT:
So, I hard-wired the lappie to get Internet access and uninstall wicd, thinking perhaps it was the problem. Installing Network-Manager didn't solve anything... at first. I read a random post instructing people to use the Hardware Driver tool to change drivers; there, I found the proprietary madwifi driver available. I switched to that and, voila, everything works. Here's my question now: why would the non-proprietary ath5k work just fine in Intrepid, but be broke in Jaunty, forcing me to go BACK to madwifi? Getting AWAY from madwifi was the REASON I upgraded from Hardy to Intrepid when Intrepid was still in beta.

---

### Post by chili555 on 2009-04-04
> #-network DISABLEDThis, typically means either the hardware wireless switch or the key combination, Fn+F5 perhaps, have switched the wireless off. Please check and see if your wireless springs to life.

---

### Post by coffeecat on 2009-04-04
Have a look at post #31 in [this thread]("http://ubuntuforums.org/showthread.php?t=1105218&page=4"). 

> **moore.bryan said:**
>  why would the non-proprietary ath5k work just fine in Intrepid, but be broke in Jaunty, forcing me to go BACK to madwifi?

Two possible reasons:

Jaunty is still in Beta. There are still bugs. Help by finding bugs and reporting them.

You upgraded. That may be the problem. A fresh install of Jaunty (A fresh install of **any** OS, Windows and MacOS included) is always more reliable. Try running live from the Jaunty CD and see if you can connect OK with the system as is. You'll be doing the community a service if you do.

---

### Post by bapoumba on 2009-04-04
Moved to Jaunty.

---

### Post by moore.bryan on 2009-04-05
> **chili555 said:**
> This, typically means either the hardware wireless switch or the key combination, Fn+F5 perhaps, have switched the wireless off. Please check and see if your wireless springs to life.
yeah, thought that might be the issue and tried it; no dice.
> **coffeecat said:**
> Have a look at post #31 in [this thread]("http://ubuntuforums.org/showthread.php?t=1105218&page=4"). 
Two possible reasons:
Jaunty is still in Beta. There are still bugs. Help by finding bugs and reporting them.
You upgraded. That may be the problem. A fresh install of Jaunty (A fresh install of **any** OS, Windows and MacOS included) is always more reliable. Try running live from the Jaunty CD and see if you can connect OK with the system as is. You'll be doing the community a service if you do.
good advice. i ran the livecd and it still didn't acknowledge any wireless cards.
> **bapoumba said:**
> Moved to Jaunty.
thank you.

---

