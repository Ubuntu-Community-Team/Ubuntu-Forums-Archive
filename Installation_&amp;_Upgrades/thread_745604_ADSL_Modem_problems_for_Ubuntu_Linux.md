---
title: "ADSL Modem problems for Ubuntu Linux"
date: 2008-04-05
forum: Installation &amp; Upgrades
---

### Post by zvacet on 2008-04-05
In upper right corner you will see network applet>left click>manual configuration>window will pop up>select your modem (don´t tick it,just click on it)>properties>select your connection(dhcp or static)>DNS tab>delete address you find there and put your nameservers>connection tab>tick your modem>window will pop up with message **changing network interfaces**>go to the terminal and type

```
pppoeconf
```

---

