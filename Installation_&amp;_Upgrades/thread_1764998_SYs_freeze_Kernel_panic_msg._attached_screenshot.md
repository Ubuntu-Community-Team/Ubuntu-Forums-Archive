---
title: "SYs freeze Kernel panic msg. attached screenshot"
date: 2011-05-22
forum: Installation &amp; Upgrades
---

### Post by Ted Zagurski on 2011-05-22
system freezes about every 20 min - screen/mouse/keyboard/hard drive all freeze. If I am in the middle of video or audio, last second of audio loops. I get a terminal screen (attached). 
Screen showes processs ID of failure (2905) with something tainted
 
This did not freeze under 10.10, but I have changed wifi card (changed driver to DRT-2870 for a D-Link BWA-125, firmware 1.3) and loaded VirtualBox from oracle (not Ubuntu - VB not running during freeze)) - no other changes.

running 11.04, classic gnome
Hardware: AMD Athlon II X4 2.8 GHz Processor
MB - MSI 785gtm-E45

---

### Post by Ted Zagurski on 2011-05-25
I got it. It was the wifi usb stick or driver, who knows. The terminal screen showed many ndiswrapper references, and since wifi is the only ndis I knew of, I got a $10 usb stick @ micro-center- Tenda w311u N/b/g (funny - it takes the same driver/chipset drt2870 as the D-link BWA-125). No software changed I pluged it in and it works great!! theres a joke about plug and play here somewhere........

---

