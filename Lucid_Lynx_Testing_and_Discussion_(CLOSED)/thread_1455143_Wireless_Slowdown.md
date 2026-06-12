---
title: "Wireless Slowdown"
date: 2010-04-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by The Pixel Developer on 2010-04-15
Hi,

**Summary**
My wireless will slow down considerably over time (10+ minutes), from 2MB/s to 100kB/s. I didn't encounter this in Karmic as far as I can remember. Running the following commands will temporary fix the issue:

[LIST]
[*]sudo rmmod rtl8187
[*]sudo modprobe rtl8187
[/LIST]

**Details**
[LIST]
[*]Using the 64 bit version.
[*]Kernel: 2.6.32-21-generic
[*]Hardware: Bus 001 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
[/LIST]

**iwconfig wlan1 dump**

[HTML]wlan1     IEEE 802.11bg  ESSID:"wireless"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:16:B6:DA:71:75   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/HTML]

**dmesg output**

[HTML][20252.288621] usbcore: deregistering interface driver rtl8187
[20252.422554] wlan1: deauthenticating from 00:16:b6:da:71:75 by local choice (reason=3)
[20253.241530] usb 1-3: reset high speed USB device using ehci_hcd and address 2
[20258.373231] phy3: Selected rate control algorithm 'minstrel'
[20258.373747] phy3: hwaddr 00:15:af:0b:35:fc, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[20258.378296] udev: renamed network interface wlan0 to wlan1
[20258.386776] rtl8187: Customer ID is 0x00
[20258.386813] Registered led device: rtl8187-phy3::tx
[20258.386831] Registered led device: rtl8187-phy3::rx
[20258.387389] rtl8187: wireless switch is on
[20258.387423] usbcore: registered new interface driver rtl8187
[20260.544152] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[20270.542339] wlan1: deauthenticating from 00:16:b6:da:71:75 by local choice (reason=3)
[20270.703286] wlan1: direct probe to AP 00:16:b6:da:71:75 (try 1)
[20270.705536] wlan1: direct probe responded
[20270.705539] wlan1: authenticate with AP 00:16:b6:da:71:75 (try 1)
[20270.707161] wlan1: authenticated
[20270.707180] wlan1: associate with AP 00:16:b6:da:71:75 (try 1)
[20270.709782] wlan1: RX AssocResp from 00:16:b6:da:71:75 (capab=0x411 status=0 aid=1)
[20270.709785] wlan1: associated
[20270.712819] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[20281.612507] wlan1: no IPv6 routers present[/HTML]

I'm pretty lost as to where to look on how to fix this issue. I can't think of anything that'd trigger it.

Any advice is much appreciated.

-Mathew Davies.

---

### Post by tjeremiah on 2010-04-15
Maybe this can help 

[http://ubuntuforums.org/showthread.php?t=1441818](http://ubuntuforums.org/showthread.php?t=1441818)

---

### Post by The Pixel Developer on 2010-04-15
Hi there tjeremiah,

I had a look and tried a few things, but none have worked. Thank you for showing me the link though.

I think it's more of a kernel driver issue. I shall be filing a bug report on the kernel bug tracker sometime later this week. I'll keep this discussion up to date if I make any headway on it.

---

