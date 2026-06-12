---
title: "Internet not working on Ubuntu 9.10"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by priteshloke on 2009-11-15
My upgrade Ubuntu 9.04 to 9.10 threw internet after successful upgrade my Internet stops working.  Is this Ubuntu 9.10 bug?
Please i need help its very urgent.

---

### Post by sanderj on 2009-11-15
Wired or wireless internet?

Post output of these three commands:

```
ifconfig
mtr -n -c3 -r 4.4.4.4
wget ubuntu.com
```


See [http://ubuntuforums.org/showthread.php?t=1309178](http://ubuntuforums.org/showthread.php?t=1309178)

---

### Post by Dale61 on 2009-11-15
If it's wireless, I posted this reply in two other threads.

I was experiencing a similar problem - happily surfing, then after x amount of time, wireless connection would drop out, unable to reconnect unless I rebooted - but have found (hopefully) a solution in another thread.

[http://ubuntuforums.org/showthread.php?t=1326114]("http://ubuntuforums.org/showthread.php?t=1326114")

Refer post #6.

---

