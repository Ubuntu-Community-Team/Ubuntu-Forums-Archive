---
title: "Multiple tmpfs mount freeze booting"
date: 2009-10-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by shram on 2009-10-27
The following cofiguration causes boot process to freeze with message: "one or more of the mounts listed in /etc/fstab cannot yet be mounted".
15G of encrypted swap space available.  Settings work fine with other OS.  Removing the second tmpfs mount on /var/tmp allows booting to proceed, but I'd really like to protect both.  

==crypttab==
cswap           /dev/sda5               /dev/urandom      cipher=aes-cbc-essiv:sha256,swap

==fstab==
/dev/mapper/cswap   none        swap    sw              0       0

tmpfs              /tmp         tmpfs   size=6144M,mode=1777          0    0

tmpfs              /var/tmp     tmpfs   size=6144M,mode=1777          0    0

---

