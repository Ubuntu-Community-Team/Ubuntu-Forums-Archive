---
title: "Feisty: asterisk, chan-capi: undefined ast_pickup_ext"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by Data on 2007-04-21
Hi,

I just upgraded to feisty an asterisk stopped working. I am running asterisk with an AVM fritz card. Capiinfo looks good, but staring asterisk gives me:

 [chan_capi.so]Apr 21 21:07:47 WARNING[14649]: loader.c:325 __load_resource: /usr/lib/asterisk/modules/chan_capi.so: undefined symbol: ast_pickup_ext
Apr 21 21:07:47 WARNING[14649]: loader.c:499 load_modules: Loading module chan_capi.so failed!

Does anybody know, what that could be? Wrong version of asterisk-chan-capi perhaps?

Michael

Ubuntu 7.04
Asterisk: 1.2.16-dfsg-1ubuntu3
ChanCapi: 0.7.1-1.1

---

### Post by beste on 2007-07-06
make sure you have a

load => res_features.so

in your modules.conf

---

