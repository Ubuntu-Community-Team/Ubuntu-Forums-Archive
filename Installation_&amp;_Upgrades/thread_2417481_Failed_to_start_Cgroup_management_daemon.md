---
title: "Failed to start Cgroup management daemon"
date: 2019-04-23
forum: Installation &amp; Upgrades
---

### Post by socrates231 on 2019-04-23
Hi,
After upgrading to 18.04 I get "Failed to start Cgroup management daemon" during  boot. It says to see 'systemctl status cgmanager.service' but I don't  know how to check it. Is there a fix ?
Some help would be great

thanks
Pietro

---

### Post by Rubi1200 on 2019-04-23
Hi and welcome to the forums :-)

From which version did you upgrade? There can often be leftover or half complete packages. Often best to backup data and do a clean install.

That said, use Ctrl+ALT+T to open a terminal and type or paste this:

```
systemctl status cgmanager.service
```

Post the results here using code tags (go advanced and look for the # symbol).

Thanks.

---

