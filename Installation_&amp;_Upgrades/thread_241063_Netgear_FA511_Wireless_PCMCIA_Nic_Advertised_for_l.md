---
title: "Netgear FA511 Wireless PCMCIA Nic? Advertised for linux bot not as adverised?"
date: 2006-08-21
forum: Installation &amp; Upgrades
---

### Post by jon_k on 2006-08-21
I got this FA511 PCMCIA card for my thinkpad t21. It said it came with linux drivers but it only comes with a .c and .h file. I really don't know how I'd put that in my kernel, not worth the trouble. I was thinking it'd have a deb, rpm, or something I could pull binaries from.

So heres my trouble. I've installed udev, module-init-tools and more. I've restarted it inside the computer. However, cardctl ident says:Socket 0:
  no product info available
Socket 1:
  no product info available
root@thinkpad:/home/jon#


Is there any way for linux to detect this card? I find people who say "woohoo it works!" while rudely omitting what they did.

Any ideas?

In addition, I've run 

root@thinkpad:/home/jon# /etc/init.d/pcmcia
 * Linux >= 2.6.13-rc1 requires pcmciautils instead of pcmcia-cs
root@thinkpad:/home/jon#

I don't understand because it's installed
root@thinkpad:/home/jon# apt-get install pcmciautils
Reading package lists... Done
Building dependency tree... Done
pcmciautils is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by jon_k on 2006-08-21
OK.. I found


card "NetGear FA511 Fast Ethernet"
  pci 0x1317, 0x1985
  bind "tulip_cb"


Within /etc/pcmcia/config

How do I activate this? Or run it?

---

