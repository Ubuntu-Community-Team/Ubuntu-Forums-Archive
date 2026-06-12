---
title: "Updates killed my wireless connection"
date: 2008-09-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by gmclachl on 2008-09-11
My wireless card seems to have stopped working. I done some updates last night and shut the machine down. When I booted up tonight it tried to connect and there were a list of wireless connections to choose from in NM.

However although it tried to connect it failed. I rebooted and now there is not even a wireless option in NM. ifconfig doesn't even list my wireless card. lspic shows the following output 

 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)


So I am kinda stumped as to what has happened. I also noticed that when I rebooted it spat out a message saying "waking up attempting normal restart"

---

### Post by ccw on 2008-09-11
> **gmclachl said:**
> I also noticed that when I rebooted it spat out a message saying "waking up attempting normal restart"

That's not related. 

I think that what's described here:
[https://launchpad.net/ubuntu/intrepid/+source/initramfs-tools/0.92bubuntu11](https://launchpad.net/ubuntu/intrepid/+source/initramfs-tools/0.92bubuntu11)

---

### Post by kangol69 on 2008-09-12
I have the same problem. I have a intelnal atheros card and it doesn't work. But I can insert my minipci atheros card and it works?????? Any ideas. My internal card doesn't even show up on lspci...


Edit : I didn't know this was the development forum. I'm still on hardy.

---

