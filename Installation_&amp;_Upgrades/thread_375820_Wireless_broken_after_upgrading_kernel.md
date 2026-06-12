---
title: "Wireless broken after upgrading kernel"
date: 2007-03-04
forum: Installation &amp; Upgrades
---

### Post by softbomb on 2007-03-04
Hi all

Been using Ubuntu for a good while now, but it works so well I've not become any sort of expert :) 

Here's my problem: I have a Thinkpad i1200 with an Origo PCMCIA wireless card running 6.06LTS which mostly worked just fine until the Update Manager installed version 2.6.15-28-386 of the kernel. The card still appears as wlan0 and looking at the Connection Properties window shows a strong signal from my wireless router, but 0 packets sent/received and status given as disconnected. 

I say the card mostly worked fine before because it wouldn't connect to the router using DHCP. Once I assigned the Thinkpad a static IP address it worked perfectly. DHCP works OK for the other computers in the house. Just thought I'd mention that - don't know if it's significant.

Any help would be greatly appreciated!

---

### Post by nyinge on 2007-03-06
Are you using ndiswrapper?  If so, you will first need to uninstall, recompile and reinstall it every time the kernel changes.

---

### Post by softbomb on 2007-03-06
No, not using ndiswrapper.

---

### Post by ffxr on 2007-03-06
what chipset does your wireless card use? did you compile the kernel modules yourself..? u will probably have to recompile the cards kernel modules... 

[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

---

### Post by softbomb on 2007-03-11
It's fixed now. My card uses the same chipset as the one mentioned in this article and I used Solution 1 on this page:

[http://guillermoesteves.com/blog/2006/06/08/how-to-get-a-d-link-dwl-g650-wi-fi-adapter-to-work-in-ubuntu-linux-6-06](http://guillermoesteves.com/blog/2006/06/08/how-to-get-a-d-link-dwl-g650-wi-fi-adapter-to-work-in-ubuntu-linux-6-06)

and it's working a treat once again. Thanks for the replies.

---

