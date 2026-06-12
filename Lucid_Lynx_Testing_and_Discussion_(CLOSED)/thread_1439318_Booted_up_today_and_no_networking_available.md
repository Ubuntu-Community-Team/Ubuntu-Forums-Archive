---
title: "Booted up today and no networking available"
date: 2010-03-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sonicb00m on 2010-03-26
I booted today and the network is completely out. I can't connect with wired or wireless. The network icon is void of anything to connect to.

Please help :D

---

### Post by Peter09 on 2010-03-26
Right click on the network icon and check that network is enabled. IF that does not fix it post the output of the terminal commands.
 
```
ifconfig
```
and
```
lshw -C network
```

---

### Post by sonicb00m on 2010-03-26
oh dude i'm actually embarrassed. The enable networking was unchecked. Can't believe I didn't see it. Thanks.

---

