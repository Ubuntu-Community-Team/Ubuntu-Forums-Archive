---
title: "No internet connection"
date: 2008-01-19
forum: Installation &amp; Upgrades
---

### Post by Didad on 2008-01-19
Simply cannot access the internet through Kubuntu. Windows XP is fine. Is there someone in Adelaide Aust who can help?

---

### Post by zvacet on 2008-01-20
In upper right side of panel is network manager icon.Click on it>manual configuration>select your modem>properties>choose what kind of connection you want (dhcp or static)>close.In DNS tab you will find one nameserver address and if you work in bridged mode delete it.Replace it with nameservers of your IP.Close and go to the general tab and tick your modem.You should see window pop up and it is saying something like **changing network interfaces**.When it is done go to the programs>accessories>terminal and type 

```
sudo pppoeconf
```

---

