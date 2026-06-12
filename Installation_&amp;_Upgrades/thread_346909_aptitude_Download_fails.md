---
title: "aptitude: Download fails"
date: 2007-01-26
forum: Installation &amp; Upgrades
---

### Post by Tetrodotoxin on 2007-01-26
Hi,

I'm having trouble installing packages with apt-get/aptitude/synaptic.Whenever multiple downloads occur at the same time (sources update, multiple packages download) I get a "remote end closed connection" error. However, the network is working fine. I worked around the problem by downloading package files one by one using wget and then installing them once whey were all on my local drive.

However, now I have to update the packages list and I'm out of ideas because the software insists on downloading them by opening several parallel connections (which fails every time).

I've tried setting Acquire::Queue-Mode both to "host" and "access", none of which works. Is there a way to tell the software to download one file at a time? Or is there another workaround?

(I'm not sure what's causing the problem but I suspect the local network configuration (which I can't influence as this is a university LAN).

greetings,
TTX.

---

### Post by lukanium on 2007-01-26
I have met this case when i was at my company. Doing something unknown about apt-get then I couldn't update or install anything. Carefully checking my apt.conf, i saw that by anyway, i had added proxy configuration to my apt.conf 
```

Accquire::http::Proxy "true";

```
So IMO check your apt.conf and try again.
Good luck ! :D

---

### Post by Tetrodotoxin on 2007-01-27
Hi,

> **lukanium said:**
> Carefully checking my apt.conf, i saw that by anyway, i had added proxy configuration to my apt.conf 
```

Accquire::http::Proxy "true";

```
So IMO check your apt.conf and try again.

Thanks for the advice. Unfortunately, that setting is definitely set to “false” on my machine, as revealed by “[FONT="Courier New"]apt-config dump[/FONT]”.

---

