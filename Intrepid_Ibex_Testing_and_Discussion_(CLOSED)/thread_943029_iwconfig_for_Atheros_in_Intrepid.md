---
title: "iwconfig for Atheros in Intrepid"
date: 2008-10-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by bob234 on 2008-10-09
Release 8.1 (intrepid)
Kernel Linux 2.6.27-6-generic

I'm using a dell laptop with a Dell Wireless 1390 wlan mini card that uses the broadcom b43 proprietary driver to connect to my G network.
I would like to connect to an N network. I have added a D-Link DWA Extreme N 643 Notebook Expresscard, with the Atheros AR5418 chipset that I understand works with the ath9k driver. I checked synaptic and I have madwifi-tools version 1:0.9.4 installed.

lspci     shows both the broadcom and atheros card
lshw -C   says the atheros network is UNCLAIMED

My question is: can anyone help me with the iwconfig commands to disable the broadcom card, and configure the atheros card so I can connect to an N network? Or maybe I have to do something to enable the ath9k driver? Any help appreciated, Thanks; Bob

---

### Post by bob234 on 2008-10-09
I should add that when I go to System/Administration/Hardware Drivers, It only shows the b43 driver, and something called wl.
I've downloaded a patch called "patch-2.6.27-rc3.bz2". I think this patch contains the ath9k driver however I don't know how to install it.It's a bz2 but it's not a tar.

---

