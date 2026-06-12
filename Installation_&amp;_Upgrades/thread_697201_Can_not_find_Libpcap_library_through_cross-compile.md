---
title: "Can not find Libpcap library through cross-compiler using Ubuntu"
date: 2008-02-14
forum: Installation &amp; Upgrades
---

### Post by nasim751 on 2008-02-14
i am using Ubuntu and after install cross compiler (hybus-arm-linux-R1.1) trying to run program under arm-linug-gcc environment and specified the right path in the ENV environment.when trying for cross-compile unfortunately can't access libpcap library. basically i am trying to run simple packet capture program and getting this type of problem .

[HTML]root@localhost:/home/nasim/Desktop/ppro# arm-linux-gcc -o snifx snifx.c -lpcap
/usr/local/hybus-arm-linux-R1.1/arm-linux/bin/ld: cannot find -lpcap
collect2: ld returned 1 exit status [/HTML] 

here in my desktop using lattest libpcap & dev library. Do you know any pre built cross-compiler version with libpcap. If yes please give the link.
regards
Ahmed

---

