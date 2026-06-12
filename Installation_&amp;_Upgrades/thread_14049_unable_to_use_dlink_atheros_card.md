---
title: "unable to use dlink atheros card"
date: 2005-02-04
forum: Installation &amp; Upgrades
---

### Post by drbart on 2005-02-04
i [re-]installed ubuntu on a really old laptop (noname, 128M, 233MHz pentium) and was unable to use my dlink dwl-g650 card.

the warty installer didn't see any sort of network card until i replaced it with my old orinoco standby.

after installation it was still uninterested in the atheros card. i tried apt-get installing madwifi but said package is unknown.

i see nothing in the logs when i plug in the card.

ideas, anyone?

---

### Post by flyfishin on 2005-02-04
The linux-restricted-modules-`name -r` package contains the madwifi drivers.

---

### Post by drbart on 2005-02-04
thanks.

apt-get install linux-restricted-modules-386 worked. also got me a new kernel.. i'm never clear on how apt treats kernel upgrades... but no complaints.

i did have to go a few rounds with ifup ath0 and trying to get the network config to automatically start the interface. i eventually modified /etc/network/interfaces by hand.

it does now start automatically on startup, but not on re-insertion. wish i knew what to poke to make this work right.

---

