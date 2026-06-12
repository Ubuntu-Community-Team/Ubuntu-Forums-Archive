---
title: "Equivalent apt-get for LAMP and OpenSSH"
date: 2010-10-29
forum: Installation &amp; Upgrades
---

### Post by cnh on 2010-10-29
Hi all,

What was the equivalent apt-get command for installing LAMP and OpenSSH in Ubuntu 10.10?

---

### Post by Jahid65 on 2010-10-29
Instead of apt-get you can use tusk-shell to install LAMP in Ubuntu.

```
sudo tasksel install lamp-server
```

Or open synaptic->edit->mark packages by task. A list will open. From there you can choose your desired one.

---

