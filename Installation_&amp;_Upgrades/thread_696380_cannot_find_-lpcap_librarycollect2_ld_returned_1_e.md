---
title: "cannot find -lpcap library
collect2: ld returned 1 exit status"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by nasim751 on 2008-02-13
i am using Ubuntu and after install cross compiler trying to run program under arm-linug-gcc environment. unfortunately can't access libpcap library using arm-linux. basically i am trying to run simple packet capture program. this type of problem getting 

  [PHP]root@localhost:/home/nasim/Desktop/ppro# arm-linux-gcc -o snifx snifx.c -lpcap
/usr/local/hybus-arm-linux-R1.1/arm-linux/bin/ld: cannot find -lpcap
collect2: ld returned 1 exit status [/PHP]
what is the issue and how can i solve this?

regards
nasim

---

