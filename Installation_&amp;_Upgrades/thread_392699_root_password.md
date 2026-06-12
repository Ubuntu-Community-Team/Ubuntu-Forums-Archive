---
title: "root password"
date: 2007-03-24
forum: Installation &amp; Upgrades
---

### Post by cornsnap on 2007-03-24
Can anyone tell me how to shutdown my server it keeps asking me for the root password?

I tried:

sudo shutdown root
sudo -i


Thanks.

---

### Post by codesplice on 2007-03-24
Have you tried
```
sudo shutdown now
```?

"shutdown" expects a time argument (such as now or a number of minutes to wait)

The password SHOULD just be your user password

---

### Post by 23meg on 2007-03-24
Type ```
sudo shutdown -h now
```and enter your *user password*.

---

