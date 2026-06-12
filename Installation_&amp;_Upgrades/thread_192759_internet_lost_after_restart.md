---
title: "internet lost after restart"
date: 2006-06-09
forum: Installation &amp; Upgrades
---

### Post by qwantum on 2006-06-09
using a cable modem. connected to pc via ethernet. dhcp enabled.

it's like this... almost everytime. (4/5 times)

after my pc started/restarted, the internet connection was somewhat lost. went to check the properties of eth0. eth0 was active. everything else looked normal too. now wat i do to get back online is...

deactivate eth0. then activate it again. and then... internet is back again...

using a sempron 3100+, asus nforce3 250.

pls help... thank you sooooooooo much.

ps: it happened right after a fresh installation.

---

### Post by drtvasudevan on 2006-06-09
i am not sure this will work for you.
disable ipv6.
open firefox. type about:config in the url box
type ipv6 in the filter
double click on the first line.
the value should toggle from false to true.
close browser.
restart firefox.

tv

---

