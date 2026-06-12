---
title: "intrepid and ieee8021.x PEAP-GTC problem"
date: 2008-10-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by fajar on 2008-10-08
Hi,

I'm testing intrepid (beta) on Acer Aspire One. With Intrepid's updated 2.6.27-6-generic kernel, I was able to get wireless working with ath5k driver.

My company uses ieee8021.x PEAP-GTC wireless security. With Hardy and network-manager 0.6.6, I can connect by choosing 
- Connect to other wireless network
- Wireless Security : WPA2 Enterprise
- EAP method : PEAP
- Key Type: Dynamic WEP
- Phase2 type : GTC

But with intrepid and network-manager 0.7, In phase2 selection there's no GTC. Any ideas how to add it back? Choosing the available MSCHAPv2 or MD5 doesn't work (obviously).

For now I've pin libnm-util0, network-manager, and network-manager-gnome to Hardy's version in /etc/apt/preferences.

---

