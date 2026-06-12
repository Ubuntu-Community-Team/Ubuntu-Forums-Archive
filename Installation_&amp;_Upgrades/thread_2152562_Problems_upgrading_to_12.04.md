---
title: "Problems upgrading to 12.04"
date: 2013-06-08
forum: Installation &amp; Upgrades
---

### Post by BruceV on 2013-06-08
Downloaded the 12.04 upgrade, on restart the system was stuck on 'waiting for network configuration', or something similar. Eventually the system started, but all connectivity was gone, couldn't even access the web through firefox. Repeated reboots / PDPU failed ot solve. Any suggestions welcome, has anyone had the same problem??

BTW, this posting is from another computer!

---

### Post by 2F4U on 2013-06-08
How are you connected to the network, wireless or wired? It seems as if you are missing some drivers, therefore some information about your hardware would be helpful.

---

### Post by Sef on 2013-06-08
What is the outcome of these commands that you can copy and paste them into the terminal:

```

lspci | grep Ethernet[COLOR=#222222][FONT=Verdana]
```

 [/FONT][/COLOR]```
[COLOR=#000000][FONT=Ubuntu Mono]sudo lshw -C network[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]```
lspci -nnk | grep -iA2 net
```
[COLOR=#222222][FONT=Verdana]

[/FONT][/COLOR]```
ifconfig
```

---

### Post by BruceV on 2013-06-08
Thanks for the responses. A reinstall solved the problem, so it's just one of those mysteries. Internet connection is wired, a single RJ cable straight to the ADSL modem. As plain vanilla as you can get.

---

