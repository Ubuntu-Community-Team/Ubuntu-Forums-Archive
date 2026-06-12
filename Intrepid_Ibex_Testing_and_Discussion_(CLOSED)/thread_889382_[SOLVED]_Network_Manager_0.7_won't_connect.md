---
title: "[SOLVED] Network Manager 0.7 won't connect"
date: 2008-08-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by zbrox on 2008-08-14
Hello everybody,

Yesterday I decided to give Intrepid some alpha testing so I upgraded from Hardy. But after the reboot network manager doesn't allow me to connect to any networks - wireless (wpa or unsecured) or wired.
My network adapter according to lshw is PRO/Wireless 4965 AG or AGN Network Connection. I guess this is an Intel product.
If I try to connect the two green dots are there as always, but it stays that way for a long time. A minute or so. Then it gives the indicator for no connection and it says the connection was interrupted.
I don't see no errors in the /var/log/messages or the syslog. Just a long attempt and then a fail.
However I'm able to connect to a wired network if in the terminal I use dhclient.

If I find out something more, I'll post it here.

---

### Post by caryb on 2008-08-14
I had to uninstall network mangler for the same reason, All works fine now!


Cary

---

### Post by zbrox on 2008-08-14
But at home I'm using a WPA encrypted wireless and I fail everytime at setting the connection in the console, so I need NM.

---

### Post by cdtech on 2008-08-14
I switched to "wicd" and mine works great now.

If you want to try "wicd" just add:
```
deb http://apt.wicd.net **hardy** extras
```
to your "/etc/apt/sources.list" file (change hardy to whatever version your running) and:
```
sudo apt-get update
sudo apt-get install wicd
```

---

### Post by zbrox on 2008-08-14
I'll give it a try right away.

---

### Post by zbrox on 2008-08-14
It's working. At least with the wired network. When I get home tonight, I'll test it with my WPA wireless one.
From a first glance however I prefer the unobtrusive NetworkManager GUI...when it's working :)
Thanks!

---

### Post by zbrox on 2008-08-16
I used Wicd for a few days and today decided to install Network Manager again and it's running fine. None of the issues are present. I don't know what was the problem but I guess some update fixed it for me.

---

### Post by olskar on 2008-08-16
Network Manager connects faster then ever for me :)

---

### Post by BC7333 on 2008-08-16
> **olskar said:**
> Network Manager connects faster then ever for me :)

Seems to be working much better here also..

2. /etc/network/interfaces is currently not recognized. Better remove all entries (except the “iface lo” one) from it to avoid confusing behaviour. The long term idea is to provide legacy backend for network-manager that parses your /etc/network/interfaces as good as possible. If thats not enough for some you probably will have to uninstall network-manager. In case our legacy backend will not reach a stable enough state for intrepid, we might go back to the dumb “blacklisting” approach we used in hardy.

Maybe helped..

[http://www.asoftsite.org/s9y/archives/149-guid.html](http://www.asoftsite.org/s9y/archives/149-guid.html)

---

