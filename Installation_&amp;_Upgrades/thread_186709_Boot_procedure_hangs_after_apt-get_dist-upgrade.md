---
title: "Boot procedure hangs after apt-get dist-upgrade"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by darkrad on 2006-06-02
Hello, i have a wifi laptop with ati card, and i upgraded last night to stable dapper release from an unstable dapper version.
After dist-upgrade got completed i rebooted, and boot sequence hangs after the line "Mounting remote file system", and after some secs the dos-like termin show up listing last command executed, hanging there for ever:

```
....
Starting raid devices...                                                           [ok]
Setting up LVM Volume Groups...                                              [ok]
Starting Enterprise Volumen Management System...                     [ok]
...done.
Traceback (most recent call last):
  File "/etc/rcS.d/S37displayconfig-hwprobe.py", line 27, in ?
     import ScanPCI
ImportError: No module named ScanPCI
Configuring network interfaces...                                              [ok]

```
plus i can't connect via ssh from another pc and if i pusch alt+canc+F* i can't have a login screen ](*,) 
Anybody has a clue of what to do?
thanks in advance

---

### Post by darkrad on 2006-06-02
Anybody have a clue please?

---

### Post by darkrad on 2006-06-02
hmm, probably the error is later of that, since it hangs after the last [ok], at "mounting remote filesystem"

---

