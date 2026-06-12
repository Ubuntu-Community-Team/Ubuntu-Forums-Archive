---
title: "update-motd, action &quot;start failed&quot;"
date: 2009-07-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by alphacrucis2 on 2009-07-13
Getting a dpkg error for update-motd (--configure) with the latest updates. Anyone else see this?

---

### Post by descendent87 on 2009-07-13
yeah just got the same thing

---

### Post by alphacrucis2 on 2009-07-13
> **descendent87 said:**
> yeah just got the same thing

I found the reason was that update-motd was already running. I fixed the problem by manually killing the process for update-motd and running the dist-upgrade again. Looks like the dpkg install script misses shutting down the existing update-motd before trying to start it.

---

### Post by descendent87 on 2009-07-13
> **alphacrucis2 said:**
> I found the reason was that update-motd was already running. I fixed the problem by manually killing the process for update-motd and running the dist-upgrade again. Looks like the dpkg install script misses shutting down the existing update-motd before trying to start it.

haha strange, just noticed the same thing and was about to post here

---

### Post by DougieFresh4U on 2009-07-13
Noticed that yesterday. Tried to kill process but it won't let me kill it, just crashes System Monitor.

---

### Post by ronacc on 2009-07-13
kill it from a terminal ```
 sudo kill -kill (process #) 
```

---

### Post by descendent87 on 2009-07-13
just had another update for ubuntu-motd which went through fine

---

### Post by DougieFresh4U on 2009-07-14
> **ronacc said:**
> kill it from a terminal ```
 sudo kill -kill (process #) 
```

Thanks, don't know why I wasn't thinking that.
All cleared up now.:)

---

