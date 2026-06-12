---
title: "Acer Aspire One D270 Network connection is fail."
date: 2017-07-18
forum: MINT
---

### Post by keyjoo on 2017-07-18
_**How to hot-fix Wi-Fi connection (Driver) in Debian systems?**_

Hello. I'm a new user in Ubuntu community. I have expirience in Linux-distrib from 2006year... But always me returned to OS Windows, because my -Nix OS was broken or network settings is wrong.. :(

_Now:_ 3 months ago I installed Linux Mint 18.1 to this Netbook **Acer Aspire One D270** 
But 2 weeks ago after regullary packages updates, my Wi-Fi connection was broken(settings or drivers). I don't know.
I want to use Linux for learning Programming, but I don't know how to fix this problem.

If I load from boot-LIVE-USB - it's all o'key! Hardware is working! 

Please look to Data-Analise of settings my Netbook Link to [PasteBin]("http://pastebin.ubuntu.com/25118533/") 

I hope it is possible!

---

### Post by praseodym on 2017-07-18
Deactivate SecureBoot in your UEFI

---

### Post by keyjoo on 2017-07-18
> **praseodym said:**
> Deactivate SecureBoot in your UEFI

:KS Well. Where are you find it?

The Model of Notebook 2012 year. BIOS without UEFI-mode.):P

---

### Post by keyjoo on 2017-07-18
[COLOR=#000000][FONT=&amp]Ok. I try get some info about my Netwark Adapters:

[/FONT][/COLOR]```
[COLOR=#2E8B57][FONT=Monaco]lspci -nnk | grep -iA2 net[/FONT][/COLOR]
```
[COLOR=#000000][FONT=&amp]and then return: 

[/FONT][/COLOR]> [COLOR=#000000][FONT=&amp]01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 05)[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Subsystem: Acer Incorporated [ALI] RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [1025:061f][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Subsystem: Foxconn International, Inc. BCM4313 802.11bgn Wireless Network Adapter [105b:e042][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Kernel modules: bcma, wl[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader [10ec:5209] (rev 01)[/FONT][/COLOR][COLOR=#000000][FONT=&amp]

[/FONT][/COLOR][COLOR=#000000][FONT=&amp]Ok, what now? [/FONT][/COLOR]):P

---

### Post by jeremy31 on 2017-07-18
See if it works after ```
sudo modprobe -v brcmsmac
```

Moved to Mint

---

### Post by keyjoo on 2017-07-19
> **jeremy31 said:**
> See if it works after ```
sudo modprobe -v brcmsmac
```


well...
```
brcmsmac not found in directory /lib/modules/4.4.0-83-generic
```
That is all what me took.

---

