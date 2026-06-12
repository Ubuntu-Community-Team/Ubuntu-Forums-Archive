---
title: "wired internet not workig"
date: 2010-09-12
forum: Installation &amp; Upgrades
---

### Post by skkmaths on 2010-09-12
i installed ubuntu 10.04 in inspiron N4010
i am getting wirles internet. But wired internet is not detecting 
at all. please help me ....
i

---

### Post by spcwingo on 2010-09-12
Please post the output of:

```
lspci
```

ran from a terminal (Applications>Accessories>Terminal)

---

### Post by iiiears on 2010-09-12
sudo ifconfig -v 
route and iptalbes are helpful here am guessing that the eth0 interface is confused about the gateway address.

---

### Post by saucywombat on 2010-09-12
I am having a similar problem. I have the exact same computer, but when I boot on ubuntu, I do not have either wireless or wired internet, even with a Ethernet cord plugged into my computer. My guess is that I need to install the drivers for the built-in wireless, but since I cannot access the Internet, I cannot download them. I also have the Drivers CD that came with my laptop if that is of any value.   Thank you in advance for any help!:D

---

