---
title: "ath9k: Unable to reset channel reset status -5"
date: 2010-01-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by t.alex on 2010-01-31
hi,

anyone else having this issue with ath9k? wireless network stops responding a few hours after boot. dmesg shows lots of

```

...
[ 7570.295883] ath9k: timeout (100000 us) on reg 0x9860: 0x00049d19 & 0x00000001 != 0x00000000
[ 7570.295888] ath9k: Unable to reset channel (5300 Mhz) reset status -5
[ 7570.295902] ath9k: Unable to set channel
[ 7570.421966] ath9k: timeout (100000 us) on reg 0x9860: 0x00049d19 & 0x00000001 != 0x00000000
[ 7570.421972] ath9k: Unable to reset channel (5320 Mhz) reset status -5
[ 7570.421981] ath9k: Unable to set channel
[ 7570.547895] ath9k: timeout (100000 us) on reg 0x9860: 0x00049d19 & 0x00000001 != 0x00000000
[ 7570.547900] ath9k: Unable to reset channel (5500 Mhz) reset status -5
[ 7570.547915] ath9k: Unable to set channel
...

``` 

remove/add ath9k seems to help at least for a few more hours.

```

lspci |grep Atheros
03:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)

```


[https://bugs.launchpad.net/mactel-support/+bug/289356](https://bugs.launchpad.net/mactel-support/+bug/289356)

---

