---
title: "Upgrade path from 7.10RC"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by mpikounis on 2007-10-19
Hi! I tried to find the answer to this but I wasn't able to. Is there an upgrade path from 7.10RC to 7.10? I tried checking for upgrades yesterday but I was told my system was up-2-date.

---

### Post by FredB on 2007-10-19
> **mpikounis said:**
> Hi! I tried to find the answer to this but I wasn't able to. Is there an upgrade path from 7.10RC to 7.10? I tried checking for upgrades yesterday but I was told my system was up-2-date.

Of course it is up to date. If you've done upgrade since you installed rc, you have the final version. For your info, final version was made on 16 october.

---

### Post by seanneko on 2007-10-19
How can you tell if you're running the final release?

I'm trying to upgrade from Kubuntu 7.10 RC to final. When I open Adept Manager and click 'fetch updates', it tells me that a new version of Kubuntu is out. After telling it to upgrade, it does various things for about a minute (downloading files, displaying licence agreement, etc), then pops up a dialogue that says "Error: Your system is up to date". If I open Adept Manager again and click 'fetch updates', the same thing will happen.

---

### Post by FredB on 2007-10-19
> **seanneko said:**
> How can you tell if you're running the final release?

Because it is the case.

> I'm trying to upgrade from Kubuntu 7.10 RC to final. When I open Adept Manager and click 'fetch updates', it tells me that a new version of Kubuntu is out. After telling it to upgrade, it does various things for about a minute (downloading files, displaying licence agreement, etc), then pops up a dialogue that says "Error: Your system is up to date". If I open Adept Manager again and click 'fetch updates', the same thing will happen.

So it is an adept bug.

In a Konsole, type this :

```
cat /etc/issue.net ; uname -a
```

Here is my output, for a Gutsy AMD64.

```
Ubuntu 7.10
Linux fredo-gutsy 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux
```

Yours could be really the same.

---

