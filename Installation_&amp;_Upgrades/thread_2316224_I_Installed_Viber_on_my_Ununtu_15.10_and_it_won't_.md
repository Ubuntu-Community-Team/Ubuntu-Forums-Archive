---
title: "I Installed Viber on my Ununtu 15.10 and it won't run"
date: 2016-03-06
forum: Installation &amp; Upgrades
---

### Post by Parker_Ong on 2016-03-06
Hi,

I downloaded the fiel on this link below:

[https://www.viber.com/en/products/linux](https://www.viber.com/en/products/linux)

Then installed it using Ubuntu Software Center. After installing it I search for the viber and the icon appeared. I clicked it and nothing is happening. No error command. I tried this several times and same thing happens. Actually nothing happens at all.

Please help.

Thanks!

Parker

---

### Post by howefield on 2016-03-06
Try installing libgstreamer-plugins-base0.10-0

```
sudo apt-get install libgstreamer-plugins-base0.10-0
```

---

### Post by Parker_Ong on 2016-03-06
WOW! It worked! What was the problem then? I'm just a new Linux User and I'm still learning how to use this. So far I'm enjoying Linux! Thanks very much!

---

### Post by howefield on 2016-03-07
> **Parker_Ong said:**
> WOW! It worked! What was the problem then? I'm just a new Linux User and I'm still learning how to use this. So far I'm enjoying Linux! Thanks very much!

You're welcome.

Looks like the package creators have missed referencing a dependency (or the dependencies have changed) from their package. Simple as that.

---

