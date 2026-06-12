---
title: "Trying to install madwifi on ubuntu server 7.10 without internet help!!!"
date: 2008-01-21
forum: Installation &amp; Upgrades
---

### Post by squideekie on 2008-01-21
I am a new linux user, i'm trying to do the recommended upgrade from ubuntu server to ubuntu studio because I don't have a dvd-writer. I succesfully partitioned and installed ubuntu server, but suring installation it didn't detect a network device. my wireless atheros 5212 based card.

here some more info:

lshw gives me:

*-network:1 UNCLAIMED
description: Ethernet controller
product: AR5212/AR5213 Multiprotocol MAC/baseband processor
vendor: Atheros Communications, Inc.
physical id: 2
bus info: pci@0000:02:02.0
version: 01
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: latency=64 maxlatency=28 mingnt=10

It shows up if I do an lspci too.

iwconfig - no wireless extensions.

modprobe ath_pci
FATAL: Module ath_pci not found.

any suggestions on how to install the madwifi drivers without internet, i have win xp as a dual boot but can't tranfer data. Could I transfer data to ubuntu server from a floppy or cd?

thanks,

---

### Post by haaglin on 2008-01-21
Install the linux-restricted-modules for your kernel from the install cd.

---

### Post by squideekie on 2008-01-21
i've done that and I've installed the madwifi drivers and it seems to be working, however i cannot update to studio: [http://www.ubustu.com/globe/2007/05/19/install-ubuntu-studio-without-a-dvd-burner/](http://www.ubustu.com/globe/2007/05/19/install-ubuntu-studio-without-a-dvd-burner/)

first command doesn't seem to have a response and the second command comes back with : "no valid OpenPGP data found"

let me know if anyone knows anything about this

Thanks

---

