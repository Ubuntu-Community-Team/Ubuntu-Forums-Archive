---
title: "How do I stop upgrade?"
date: 2011-03-17
forum: Installation &amp; Upgrades
---

### Post by reedk on 2011-03-17
Now, every time I run update manager, it tells me to run a partial upgrade. I can close the window and proceed upgrading packages,but if I let it try the partial upgrade is starts a distribution upgrade !??! I am currently running 11.04.

How can I stop update manager from trying to update my distro version?

---

### Post by user1397 on 2011-03-17
> **reedk said:**
> Now, every time I run update manager, it tells me to run a partial upgrade. I can close the window and proceed upgrading packages,but if I let it try the partial upgrade is starts a distribution upgrade !??! I am currently running 11.04.

How can I stop update manager from trying to update my distro version?
well since 11.04 is the development release, it is the highest version currently available, so you can't really 'upgrade' into anything else.  i would just let it do all the upgrades it asks for, as they're constantly updating 11.04 as they're preparing it for the official release in late April.

btw are you running this as your main OS? that is highly ill advised, as it is very prone to crashing and other issues.

---

### Post by reedk on 2011-03-17
Thanks ubuntuman. I mis-typed. I am using 10.04 LTS (Lucid). It's been pretty good for me. I have been using ubuntu since 8.04 so I'm pretty comfortable with it; I just don't know how to un-set this behavior.

---

### Post by matt_symes on 2011-03-17
Hi

Have a look on the software source->Upgrades page and see what is set there.

Kind regards

---

### Post by reedk on 2011-03-17
I checked and "Release Upgrade" was already set to "Long term support releases only". Good thought, tho.

---

### Post by matt_symes on 2011-03-17
Hi

Post the output of 

```
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d
```

Maybe you have inconsistencies in your sources

Kind regards

---

### Post by reedk on 2011-03-18
Props to matt_symes on this one. He suggested posting the output of
```

cat /etc/apt/sources.list
ls /etc/apt/sources.list.d

```Prior to posting it, I went through a manual comparison myself, starting with a cleanup of all the entries in *sources.list.d* that I was no longer using. After cleaning it up I re-ran  Update Manager. It no longer wants to attempt a distribution upgrade.

My recommendation to anyone having this issue is to start by removing any stale or unneeded repositories from *sources.list.d. *If you still have a problem then you have a different problem and you should post your sources as described above.

---

