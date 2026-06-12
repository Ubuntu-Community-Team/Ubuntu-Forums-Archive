---
title: "apt-get"
date: 2010-11-10
forum: Installation &amp; Upgrades
---

### Post by Bunzinator on 2010-11-10
I've been having an intermittent issue with apt-get recently, on my machines at home which use a satellite connection.

It sits here, waiting for headers, for several minutes before failing the connection and starting on the next 4, which wait for headers, etc. 

```
ian@osiris:/var/lib/apt/lists$ sudo apt-get update
0% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers]
```

I believe it's related to the latency of my connection, which is often 1500-3000ms. 

Does anyone have any ideas on tuning timeouts etc? I've browsed the apt doco, but haven't found anything that helps.

Thanks in advance,
Ian

---

### Post by sikander3786 on 2010-11-10
It might be related to connection's latency.

But did you try switching to some other update server from Software Center > Edit > Software Sources?

---

### Post by Bunzinator on 2010-11-11
> **sikander3786 said:**
> It might be related to connection's latency.

But did you try switching to some other update server from Software Center > Edit > Software Sources?

Hi. yes, I tried a few different ones, same result. The latency difference between the different repositories is pretty insignificant compared to the satellite latency.

I'll have to start running mtr in conjunction with my update attempts to see if I can see any correlation between ping times and failure.

---

