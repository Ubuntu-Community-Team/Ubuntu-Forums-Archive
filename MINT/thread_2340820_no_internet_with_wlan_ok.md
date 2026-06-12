---
title: "no internet with wlan ok"
date: 2016-10-22
forum: MINT
---

### Post by rolandruiken on 2016-10-22
Hello,

used on Acer Aspire linux mint xfce 18 from USB everything worked.

Installed it on the harddisk - and now it seems to work not everything:

The wlan connects fine - but it is not able to go to the internet. Tried different wlans.

Internet works fine with ehternet cable.   What could be the reason

---

### Post by Hadaka on 2016-10-22
Hi, please post the output of..
```
lspci -nnk | grep -iA2 net
rfkill list all
```
thanks.

---

### Post by howefield on 2016-10-22
Thread moved to the "*MINT*" sub forum.

---

