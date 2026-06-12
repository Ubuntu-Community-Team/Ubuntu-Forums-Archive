---
title: "Upgrade Ubuntu server 8.04.1 to 8.04.4"
date: 2010-03-11
forum: Installation &amp; Upgrades
---

### Post by dalitso on 2010-03-11
I am failing to upgrade my Ubuntu server 8.04.1 to 8.04.4

```
apt-get update
```
and
```
apt-get upgrade
```

are not doing it. It just updates the packages, kernel..

Any help will be appreciated.

---

### Post by slakkie on 2010-03-11
what does lsb_release -a say?

---

### Post by dalitso on 2010-03-11
```
root@wani:~# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.4 LTS
Release:        8.04
Codename:       hardy

```

It seems like it was upgraded all along. Webmin has been deceiving me its still shows 8.04.1.

Thanks for the the lsb_release -a command. I didn't know about it.

---

### Post by slakkie on 2010-03-11
> **dalitso said:**
> ```
root@wani:~# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.4 LTS
Release:        8.04
Codename:       hardy

```

It seems like it was upgraded all along. Webmin has been deceiving me its still shows 8.04.1.

Thanks for the the lsb_release -a command. I didn't know about it.

Reload webmin? It should look in the file /etc/lsb_release.

---

### Post by dalitso on 2010-03-12
Cool, thanks

---

