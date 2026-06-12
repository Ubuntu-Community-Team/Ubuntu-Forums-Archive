---
title: "apt update hangs after &quot;Hit:4 http:/...InRelease&quot;"
date: 2016-05-19
forum: Installation &amp; Upgrades
---

### Post by ptomblin on 2016-05-19
I upgraded from 15.10 to 16.04 this afternoon. This evening I notice that whenever I try ```
apt-get update
``` or ```
apt update
``` it hangs after 
```
Hit:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease               
Hit:3 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease             
Hit:4 http://security.ubuntu.com/ubuntu xenial-security InRelease               

```

I removed the third party sources from /etc/apt/sources.list.d

I swear this was working before I left for dinner.

---

### Post by Brandon_MacEachern on 2016-05-19
Somethings wrong on the server.  Entire rack at work, all new machines just unboxed, are doing the same exact thing.

---

### Post by The Cog on 2016-05-19
[http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) gives me the same problem. So it's not just a US server, it's something that's been rolled out to the repository mirrors too.
See this thread for a work-round: [http://ubuntuforums.org/showthread.php?t=2325168](http://ubuntuforums.org/showthread.php?t=2325168)

---

