---
title: "How To Recognize Wifi"
date: 2006-02-19
forum: Installation &amp; Upgrades
---

### Post by tvsidekick on 2006-02-19
I am now on the forum using Windows on my dual-boot. I can't seem to figure out how to get my Belkin PCI wifi to be recognized by Firefox on ubuntu. The card appears in network ("tools?") with the generic 127.0.0.1 address and as a loopback device, and pings very nicely, thank you.  Do I need to add it in network devices as a new device? Help says to hit the "add" button in the device tab, but there is no "add" avaliable.  All that appears on the divice list is two ethernet ports and a modem.

---

### Post by stangbang on 2006-02-19
the loopback adapter is not your nic card. You probably need to use ndiswrapper to get your wireless nic set up, and the recompile the kernel to make it work. If you do a search on the forum, or google you should be able to fine tutorials on doing both of these things (if not one dealing with both).

---

