---
title: "Proftpd broken?"
date: 2007-06-08
forum: Installation &amp; Upgrades
---

### Post by tommi-fi on 2007-06-08
Hey,

I have a problem with proftpd.
```
htpc:/etc$ proftpd
 - notice: unable to bind to Unix domain socket at '/var/run/proftpd/test.sock': Permission denied
 - notice: unable to listen to local socket: Permission denied
 - Fatal: SystemLog: unable to redirect logging to '/var/log/proftpd/proftpd.log': Permission denied on line 87 of '/etc/proftpd/proftpd.conf'
```

I have installed proftpd using apt-get. In Ubuntu 5.04 it worked out of the box when using local user accounts. I can post my proftpd.conf if necessary. 

Hardware I'm runnig is Fujitsu ICL ergoproX witd 10G HD 256M RAM and integrated Intel Pro100 network.

---

### Post by richrider on 2007-10-17
Any luck with this issue because I find I'm having the same problem.

Rich

---

### Post by trymbill on 2007-10-18
Don't you just have to use "sudo" ?

Like: sudo /etc/init.d/proftpd start

---

