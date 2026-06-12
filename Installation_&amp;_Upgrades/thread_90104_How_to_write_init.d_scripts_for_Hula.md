---
title: "How to write init.d scripts for Hula"
date: 2005-11-14
forum: Installation &amp; Upgrades
---

### Post by motor9805 on 2005-11-14
Unable to obtain Hula binary install packages for Ubuntu, there's the broken packages. 

Download and install source packages, system working well, but the problem is have to manually start hula services (via deamon):

..\hulamanager -d

Any one can help: 

How to start Hula services automatically? using "init.d scripts" ?

Thx!

Regards,

---

### Post by oskude on 2005-11-14
a VERY simple /etc/init.d/hula script could be```
#!/bin/sh
case "$1" in
start)
path/to/prog/hulamanager -d
;;
stop)
;;
restart)
;;
esac

```

and for howto start that automaticly, search the forums or wiki. there *should* be an answer...

---

