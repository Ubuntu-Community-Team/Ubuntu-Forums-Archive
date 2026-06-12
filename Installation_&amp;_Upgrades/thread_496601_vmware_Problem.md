---
title: "vmware Problem"
date: 2007-07-09
forum: Installation &amp; Upgrades
---

### Post by ali780 on 2007-07-09
[SIZE="4"]Hi
I.ve installed vmware server but when I run it in command widows I receive:

vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.


How can I fix it?
Thanks[/SIZE]

---

### Post by dabl on 2007-07-09
```
sudo /usr/bin/vmware-config.pl
```

:)

---

### Post by ali780 on 2007-07-09
[SIZE="4"]I did it but the problem persist.[/SIZE]

---

### Post by overkillm on 2007-07-09
Did you have VMWare Player installed before you installed VMWare Server?  If so, the following thread might help you.  I know it helped me when I had this very same problem:

[http://www.debuntu.org/vmware-server-not-starting-after-reboot](http://www.debuntu.org/vmware-server-not-starting-after-reboot)

If not...umm.. I'm stumped.  :)

---

### Post by ghost_ryder35 on 2007-07-11
you need to run the script that it is telling you too run, make sure you know the location of your header files just incase the file doesnt :)

---

