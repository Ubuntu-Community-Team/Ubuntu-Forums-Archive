---
title: "LinuxMint rt2800pci wireless issue"
date: 2015-08-31
forum: MINT
---

### Post by Kaijday on 2015-08-31
I have been running just windows recently and decided to go back to Linux after university. So i purchased a new SSD and installed LinuxMint alongside my old Windows partition.

I have used Linux on this Wireless Card before and it was fine! I've used Ubuntu/Mint and most recently Arch (had the same wireless card for circa 4 years now with no troubles ever)

Under mint sometimes it shows a list of APs, sometimes not. Veryy rarely it will connect, but alas no internet. Most of the time it will just attempt to connect and then fall short.

LSPCI :

> 04:07.0 Network Controller: Ralink corp, RT3060 Wireless 802.11n 1T/1R

iwconfig :
> wlan0        IEEE 802.11bgn    ESSID: off/any
                                  Mode: managed    Access Point: Not-associated    TX-power=20dBm
                                  Retry short limit:7    RTS thr:off     Fragment thr:off
                                  Power management:off

lspci -v:
> lspci -v
05:02.0 Network controller: Ralink corp. RT3060 Wireless 802.11n 1T/1R
    Subsystem: Edimax Computer Co. Device 7711
    Flags: bus master, slow devsel, latency 32, IRQ 21
    Memory at ff9f0000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: rt2800pci


---

### Post by howefield on 2015-08-31
Thread moved to the "*MINT*" forum.

---

### Post by trtle on 2015-09-09
three years ago the Railink driver was experimental according to this post:  [http://askubuntu.com/questions/84959/how-do-i-get-a-ralink-rt3060-wireless-card-working#answer-175399](http://askubuntu.com/questions/84959/how-do-i-get-a-ralink-rt3060-wireless-card-working#answer-175399) 
and they were using the rt2800pci driver for the rt3060, like you.

This is a walk-thru for getting RT3060 to work, and like you the person was using rt2800pci driver
[URL="http://ubuntuforums.org/showthread.php?t=2088917"]http://ubuntuforums.org/showthread.php?t=2088917
[/URL]
In this last link, he gets it working but how it doesn't really tell in the article, maybe he went back to the beginning and tried something else in the first link, above?

---

