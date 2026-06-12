---
title: "Really Slow Samba"
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by thavinci on 2008-06-09
Just crossing over from FreeBSD for my file server.

I updated apt-get and installed samba.
After all done , i tried to use it.

Man ive never seen anything this slow must of the time i got 1M and under!!! , And here i was moaning about 14M!

After more research, it seems it could be samba thats the guilty party.

iperf revealed 160M throuput with BSD aswell as ubuntu, so no downfall there.

I have got a realtek 8169 chipset for NIC and i beleve there is an issue with Samba and this chipset.
Appologies lspci revealed following as NIC...
"00:07.0 Ethernet controller: D-Link System Inc DGE-528T Gigabit Ethernet Adapter (rev 10)"



Off to check my version i discovered i have version Version 3.0.28a

However on samba wesite Samba 3.0.30 is already out.

I did the usual apt-get update 
apt-get install samba

only to be told i already have latest version.

FFS i dont!

Hopying new samba will solve my issues but can't get apt-get to realise new version out.


Help!?

---

