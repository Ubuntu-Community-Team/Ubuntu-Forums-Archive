---
title: "Help with alternate installer!!!"
date: 2011-10-12
forum: Installation &amp; Upgrades
---

### Post by mohit.shurtugal on 2011-10-12
Hi,

I just got myself a new computer ( i5 2500k, 8 GB RAM, NVIDIA GT 240, Gigabyte z6

I tried installing Ubuntu 10.10 on it but after the initial splash screen i got a grey unresponsive screen- I assume the Ubuntu installer has issues with my hardware.

I could get Debian installed but was not too happy.

I finally got to know about the Ubuntu Alternate install which is similar to the debian installer( debian installed nice and smooth on my machine) and downloaded it, used unetbootin and booted into it. Finally I reached a point where it wants to download installer components:

Can't i have a totally offline install?

If i cant: the how to i specify my proxy to the installer as it keeps saying bad internet connection each time- It wants the proxy in the standard form of "http://[[user..../"
My proxy address is 10.3.100.212 with a port of 8080 and no usernane and password.

Thanks in Advance

---

### Post by collisionystm on 2011-10-12
You can have an offiine install. Just disconnect your network cable. and setup wont try to download anything

---

### Post by Dangertux on 2011-10-12
> **mohit.shurtugal said:**
> Hi,

I just got myself a new computer ( i5 2500k, 8 GB RAM, NVIDIA GT 240, Gigabyte z6

I tried installing Ubuntu 10.10 on it but after the initial splash screen i got a grey unresponsive screen- I assume the Ubuntu installer has issues with my hardware.

I could get Debian installed but was not too happy.

I finally got to know about the Ubuntu Alternate install which is similar to the debian installer( debian installed nice and smooth on my machine) and downloaded it, used unetbootin and booted into it. Finally I reached a point where it wants to download installer components:

Can't i have a totally offline install?

If i cant: the how to i specify my proxy to the installer as it keeps saying bad internet connection each time- It wants the proxy in the standard form of "http://[[user..../"
My proxy address is 10.3.100.212 with a port of 8080 and no usernane and password.

Thanks in Advance

You got the answer about offline installation, simply choose not to configure network at this time, or like the other poster said disconnect yourself from the network.

If you wish to specify a proxy, you should during the alternate installation process have the option to do so. If your proxy does not use a username / password, then simply do not provide one.

Hope that helps.

---

