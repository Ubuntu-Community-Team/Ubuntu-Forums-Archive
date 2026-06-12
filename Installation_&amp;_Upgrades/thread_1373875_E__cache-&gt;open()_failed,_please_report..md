---
title: "E: _cache-&gt;open() failed, please report."
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by Gersoni on 2010-01-06
Hello.

I installed Ubuntu some days ago. It is really great, so much better then Vista :)

But, I´ve got a small problem.

When I try to install/update software, I get the following error:

> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.It is very annoying, since I can´t install software now :(

Can someone provide me the solution?

Thank you in advance

---

### Post by howefield on 2010-01-06
The solution is in the error, it is telling you what to do.

Open a terminal (Applications > Accessories > Terminal) and type

```
sudo dpkg --configure -a
```

Enter your password if prompted.

---

### Post by Gersoni on 2010-01-06
> **howefield said:**
> The solution is in the error, it is telling you what to do.

Open a terminal (Applications > Accessories > Terminal) and type

```
sudo dpkg --configure -a
```Enter your password if prompted.

Of course I tried that, but it told me:

> dpkg: parse error, in file '/var/lib/dpkg/updates/0020' near line 0:
 newline in field name `'

What now?

---

### Post by Gersoni on 2010-01-08
Please, anyone?

---

