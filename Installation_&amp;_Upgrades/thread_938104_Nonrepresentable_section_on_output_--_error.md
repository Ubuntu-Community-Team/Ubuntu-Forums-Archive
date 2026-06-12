---
title: "Nonrepresentable section on output -- error"
date: 2008-10-04
forum: Installation &amp; Upgrades
---

### Post by Morfi777 on 2008-10-04
Hi

I searched even on google and I didn't find excatly my problem. So rare huh ?

Here is the error log.
```
admin@ks39028:~/Desktop/ghost_v8/ghost$ make
g++ -o ./ghost++ bncsutilinterface.o bnet.o bnetprotocol.o commandpacket.o config.o crc32.o csvparser.o game.o gameplayer.o gameprotocol.o gameslot.o ghost.o ghostdb.o ghostdbsqlite.o language.o map.o socket.o stats.o statsdota.o util.o sqlite3.o -L. -L../bncsutil/src/bncsutil/ -L../StormLib/stormlib/ -lbncsutil -lpthread -ldl -lStorm
/usr/bin/ld: ./ghost++: hidden symbol `fstat64' in /usr/lib/libc_nonshared.a(fstat64.oS) is referenced by DSO
/usr/bin/ld: final link failed: Nonrepresentable section on output
collect2: ld returned 1 exit status
make: *** [ghost++] B\u0142\u0105d 1

```


Thanks in advance for help

---

