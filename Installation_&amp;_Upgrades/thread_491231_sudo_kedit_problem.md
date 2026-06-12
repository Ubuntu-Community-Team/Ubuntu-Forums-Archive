---
title: "sudo kedit problem"
date: 2007-07-03
forum: Installation &amp; Upgrades
---

### Post by zl2k on 2007-07-03
hi, all
I have no problem to open kedit from the command line, however, when I do```
sudo kedit
``` here is what I got
```
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-9426' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.

```

Can someone please help me to fix this problem? I am using kubuntu 7.04 on Toshiba Satellite s2386.

zl2k

---

### Post by LaRoza on 2007-07-03
```

gksudo kedit

```

---

### Post by walkerk on 2007-07-03
gksudo wont fix it.. just a different way of entering your root password..

---

### Post by LaRoza on 2007-07-03
> **walkerk said:**
> gksudo wont fix it.. just a different way of entering your root password..

You're right, I thought that might be the issue.

[http://ubuntuforums.org/archive/index.php/t-247649.html](http://ubuntuforums.org/archive/index.php/t-247649.html) very similar post.

---

### Post by dabl on 2007-07-03
```
kdesu kedit
```

KDE apps (as opposed to CLI bash commands) are looking for a "kdesu" to run in Super User mode.:)

---

