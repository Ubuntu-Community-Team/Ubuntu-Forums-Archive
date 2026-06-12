---
title: "How can I change the DNS server command?"
date: 2010-02-15
forum: Installation &amp; Upgrades
---

### Post by tokijitza on 2010-02-15
[B][SIZE=3]How can I change the DNS [server]("http://www.ubuntux.org/node/9266#") command because every time I restart my computer I have to write this in the terminal: [/SIZE][SIZE=3][COLOR=Red]sudo gedit /etc/resolv.conf[/COLOR][/SIZE][SIZE=3]
[/SIZE][/B]

                                                     [FONT=Verdana][SIZE=3] Please help:)[/SIZE][/FONT]

---

### Post by zvacet on 2010-02-16
After you connect ou can try this

```
/etc/init.d/networking restart
```

---

### Post by darkod on 2010-02-16
You want to use different DNS servers than the ones allocated by your ISP?
Right click Network Manager icon in top right and select Edit Connections, or open Network Settings from System-Administration.
Select your connection, click Edit.
Select the IPv4 tab.
In the drop down list instead of Automatic DHCP select Automatic DHCP addresses only. That will get only your IP from the provider, not the DNS servers.
At the bottom of the windows there is a DNS field where you can enter the IPs of the DNS servers you want to use. You can enter more than one server with ; between them.
Click on OK or Close to close all the windows and that's it. Those settings will remain even after restarting so you shouldn't need to do it every time you boot.

---

### Post by presence1960 on 2010-02-16
> **tokijitza said:**
> [B][SIZE=3]How can I change the DNS [server]("http://www.ubuntux.org/node/9266#") command because every time I restart my computer I have to write this in the terminal: [/SIZE][SIZE=3][COLOR=Red]sudo gedit /etc/resolv.conf[/COLOR][/SIZE][SIZE=3]
[/SIZE][/B]

                                                     [FONT=Verdana][SIZE=3] Please help:)[/SIZE][/FONT]

[https://store.opendns.com/setup/operatingsystem/ubuntu](https://store.opendns.com/setup/operatingsystem/ubuntu)

scroll down to #8. That is what I did when I switched to OpenDNS.

---

### Post by tokijitza on 2010-02-16
Thank you guys.. Blagodaria ti darko. Tvoqta informaciq beshe mnogo polezna :)

---

