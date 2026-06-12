---
title: "Intrepid not supporting 3com wlan usb- adapters?"
date: 2008-10-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by howbag on 2008-10-26
Hello! I updated recently to the intrepid RC. My wlan-adapter 3Com 3CRSHEW696, which always has worked out-of-the-box since ubuntu 5, was now having issues with the network manager (or so I guess)

Problem:
The adapter is found using ifconfig, and finds my ESSID using iwlist scan. A dhcp-query is too much though, and cant be done through network manager or command line (sudo dhclient wlan0). Giving in a static IP-adress, network manager says I'm connected (6%) - but I have no contact with my router or the world. Anyone knows anything about this?

---

