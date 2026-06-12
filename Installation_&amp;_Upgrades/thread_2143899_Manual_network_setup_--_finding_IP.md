---
title: "Manual network setup -- finding IP"
date: 2013-05-10
forum: Installation &amp; Upgrades
---

### Post by dodgingspam on 2013-05-10
Due to a tiny hard drive I an trying to install alternative version of Lubuntu 12.04. Everything goes well untill I get to the part where it attempts to instal network. It fails doing it automatically, complaining about something like DHCP,  and I have to go manually. The first question is asks is IP. There's no OS on this laptop yet, how can I find it's IP? Or is it asking for IP of the wireless network that I use? Sorry, I'm a novice when it comes to hardware.

Thanks.

---

### Post by steeldriver on 2013-05-10
It needs any valid unused IP in the IP range of the network you are trying to connect it to - usually a regular consumer-grade router hands out addresses in the private LAN IP range 192.168.0.xxx or 192.168.1.xxx

If you have any other devices on the network already you can make an educated guess based on their addresses, or even better if you can access the router's setup and see what it's LAN pool is set to and whether it reserves any part of the range for static addressing

OTOH if you are connecting direct to a modem with an ISP-supplied public IP then things will be more complicated

---

### Post by dodgingspam on 2013-05-10
No, I do not connect with a cable, there's a wireless network. Is it the same IP as when I go to google and search for MY IP and get -- Your public IP address is 00.000.000.00 ? The problem is I'm not even sure how t access router setup. It's connected to a cable and wireless router is plugged into it. So, when I try to look at the Properties of that wireless connection I see no IP info.

---

### Post by darkod on 2013-05-10
No, it's not your public IP. The public IP is what is says, your public IP towards the internet. Your home LAN has private addresses otherwise how can you have more then one devic? An IP can't be the same for two devices, public or private.

Did you connect the computer to your wi-fi network? If you did, it should receive available address by dhcp automatically. if it doesn't, either it's not connected to the wi-fi network correctly, or your dhcp server is not working correctly.

In any case you should be able to continue with the install. Just tell it you will set up networking later and that's it.

---

### Post by dodgingspam on 2013-05-10
Gotcha. Yes, it does not appear that it connected to wireless yet. I'll try to skip the step. Thanks.

---

### Post by dodgingspam on 2013-05-10
OK, I was able to complete the installation, however, when it loads now, everything is a command line interface... -bash Is that it's supposed to be?

---

### Post by dodgingspam on 2013-05-10
OK, I was able to complete the installation, however, when it loads now, everything is a command line interface... -bash Is that it's supposed to be? After reading a lot of posts it seems what I really need is a UNR. Can't find it anywhere.... all links are broken.  :(

---

### Post by darkod on 2013-05-11
Is this alternative version of Lubuntu released by Canonical? Or you meant Lubuntu itself as laternative to Ubuntu?

Depending how the OS is developed, it might not include desktop environment by default. The official Lubuntu includes that, I have not sure what you are installing exactly because you say "alternative version to Lubuntu".

---

