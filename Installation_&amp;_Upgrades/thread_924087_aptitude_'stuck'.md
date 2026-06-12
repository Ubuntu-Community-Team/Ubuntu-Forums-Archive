---
title: "aptitude 'stuck'"
date: 2008-09-19
forum: Installation &amp; Upgrades
---

### Post by robinc on 2008-09-19
Morning all!


Any package I try and install with aptitude I get this error

```

khtml2png: Depends: kdelibs4c2a but it is not going to be installed
Depends: libkonq4 but it is not going to be installed

```

khtml2png is a package I tried to install but failed!

but whatever I try and install from now on...fails :(

I've tried **sudo aptitude clean**

I'm running Ubuntu Server 8.04 x84.

Any help greatly received.

---

### Post by Partyboi2 on 2008-09-19
have you tried
```
sudo aptitude install -f
```

---

### Post by robinc on 2008-09-19
> **Partyboi2 said:**
> have you tried
```
sudo aptitude install -f
```

I did..and it didn't seem to do anything.

I did again and now it's worked.

I am an idiot.

and thank you so much.

---

### Post by Partyboi2 on 2008-09-19
Your welcome :)

---

