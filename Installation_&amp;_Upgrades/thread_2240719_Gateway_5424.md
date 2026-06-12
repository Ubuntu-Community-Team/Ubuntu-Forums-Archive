---
title: "Gateway 5424"
date: 2014-08-21
forum: Installation &amp; Upgrades
---

### Post by reynier2 on 2014-08-21
Hi, I need some help with 14.04 install. My computer is a gateway5424 with intel core duo processor E6400 and nvidia geforce 7300LE and 4g ddr2. Previously I had 12.04 and 13.10 and went onto install 14.04 and also erasing the older versions. When booting I get the following: cannot load firmware file gene_15.fw and then when I type my password it opens but it just shows the background, no cursor, no nothing. I tried most of the solutions offered including purging nvidia but nothing resolves the problem. Any help will be greatly appreciated, thanks[h=1][/h]

---

### Post by mörgæs on 2014-08-23
Hi, welcome to the fora.

Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags. Can be done from a live boot.

---

