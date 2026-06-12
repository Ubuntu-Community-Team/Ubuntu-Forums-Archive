---
title: "Terminal Mode"
date: 2008-02-25
forum: Installation &amp; Upgrades
---

### Post by wbrouwer on 2008-02-25
After installing the KDE libraries on my Ubuntu 7.10 install the ALT-CTRL F2 no longer works.  All I get is a blank screen.  Pressing ALT-F7 returns me to the graphical screen.  Same thing occurs when pressing ALT-CTRL F3 to F6.  The terminal options still works from Applications/Accessories/Terminal.

Any suggestions would be appreciated.

Thanks in advance.

---

### Post by jpeddicord on 2008-02-26
Could you run the following commands and paste the output here?

```
ps -A | grep getty
```
```
ls /etc/event.d
```

---

