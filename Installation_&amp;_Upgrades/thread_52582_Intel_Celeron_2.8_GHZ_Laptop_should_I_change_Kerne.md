---
title: "Intel Celeron 2.8 GHZ Laptop should I change Kernel?"
date: 2005-07-28
forum: Installation &amp; Upgrades
---

### Post by kagashe on 2005-07-28
Hi,

I have installed Ubuntu 5.04 in normal mode on my Laptop and I can connect to internet, use Evolution etc. I am using GTRAN mobile instrument to connect to internet. It gets detected as ttyACM0. Earlier, I was using the RConnect script for connecting but not getting enough speed (The mobile is capable of 112 Kbps). The Rconnect script was supplied by the ISP. Later on, I have configured wvdial and I am getting the speed upto 112 Kbps now. I find that wvdial is not using the /etc/ppp/pap-secrets and /etc/ppp/chap-secrets files (set up by RConnect script). Anyway, I am very happy as far as surfing the net is concerned.

When I tried Totem Movie Player to play VCD it could not.
I find that Open Office is slow but this may be due to less RAM (128 MB) as I have read elsewhere on the forum that Gnome desktop requires 256 MB RAM.

Presently following kernels are installed:
linux-image-2.6.10-5-386 2.6.10-34
linux-image-386 2.6.10-7

I would like to know whether I should install the following kernels through Synaptic Package Manager since it is Intel Celeron 2.8 GHz Laptop.
linux-image-2.6.10-5-686 2.6.10-34
linux-image-686 2.6.10-7

Will it help running Totem Movie Player, Open Office etc?
How it will affect connecting to net through wvdial?
(I am more concerned with this aspect).

kagashe

---

### Post by mamato on 2005-07-28
Changing kernel is not the one-stop solution for making your laptop works faster. It will help indeed, but IMHO there are some ways that you can do for making your laptop works faster:
1. Remove all services you don't need. Use **sudo update-rc.d -f name_of_service remove** to remove the service. The name of services is under the **/etc/init.d/** directory. Or perhaps you can try Boot Up Manager (BUM), take a look at the  [home page](http://www.marzocca.net/linux/bum.html).
2. Set vm.swappiness on your laptop. Use a number range between 0-100, and write **vm.swappiness=30** in **/etc/sysctl.conf**.
3. Use hdparm for increasing your harddisk speed.
4. Read some articles on Customization & Tricks Section

Hope that's help  ;-)

---

