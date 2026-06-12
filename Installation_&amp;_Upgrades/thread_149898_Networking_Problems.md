---
title: "Networking Problems"
date: 2006-03-24
forum: Installation &amp; Upgrades
---

### Post by rianquinn on 2006-03-24
Ok I have two problems here that I need help with. First, the only way I get my wired lan to work is by typing 

```
sudo dhclient
```

How can I get this to work automatically. My connection name is eth1

More importantly, I am having problems with ndiswrapper. I installed ndiswrapper-utils. And I ran without error the following:

```

ndiwrapper -i mydriver.inf
ndiswrapper -l
modprobe ndiswrapper
ndiswrapper -m

```

Everything worked fine, but I get nothing from the wireless card. No lights are on, and iwconfig doesn't show wlan0. What should I do? 

Thanks Everyone

---

