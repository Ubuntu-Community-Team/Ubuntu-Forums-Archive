---
title: "atheros connect to secure network"
date: 2009-04-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by atomizer on 2009-04-17
Hi.


I did an upgrade to kubuntu 9.04 and the wireless Atheros AR5007 did not work any more

So I   removed the atheros driver in jockey and installed linux-backports-modules-jaunty, just as I did in intrepid and before.

Now I can see the access points in knetworkmanager (whitch btw does not start at boot), but I am unable to connect to secure networks. Unsecure no problem.

Anyone knows a solution?

---

### Post by atomizer on 2009-04-18
bump

---

### Post by atomizer on 2009-04-18
So is there someone who can tell me how they got their AR242x wireless working? (or do all of you betatesters use another wifi card?)

madwifi doesn't work
atheros restricted drivers doesn't work
linux-backports-modules-jaunty: I can see the routers in my neighbourhood, but can only connect to unsecured networks


Encryption is WPA/RSN

---

### Post by atomizer on 2009-04-20
bump (maybe someone who encountered this problem too?)

---

### Post by raiwo on 2009-04-20
> **atomizer said:**
> So is there someone who can tell me how they got their AR242x wireless working? (or do all of you betatesters use another wifi card?)

my card is AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

installed beta, and it worked right out of box (first time in ubuntu when wifi just works fo me) using ath5k_pci driver & connects just fine to WPA encrypted network.

Sorry that cant help you

---

### Post by atomizer on 2009-04-20
I will try with an fresh install when 9.04 is out.

maybe there are issues whith linux-backport-modules when doing an upgrade from 8.10, i am just guessing.



with fresh install I can use ext4 too, wanna try that anyways

---

