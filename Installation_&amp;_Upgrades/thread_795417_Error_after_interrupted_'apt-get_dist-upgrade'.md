---
title: "Error after interrupted 'apt-get dist-upgrade'"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by derjoerg on 2008-05-15
Hi,

some days ago my laptop with 8.04 installed stops working while executing an
```

sudo apt-get dist-upgrade

```

Since then always when I rerun the above stated statement I get an error-message from apt-get saying that
```

Can not stat »./usr/share/evolution-data-server-2.22« (which I just tried to install): Permission denied 

```

After looking at the named file I saw the following after an
```

ls -l /usr/share

```
I see the following

```

??????????    ? ?    ?        ?                ? evolution-data-server-2.22 

```

I can not delete the file "Permission denied", even as root it is not allowed :confused:

I tried a lot of different params with "dpkg" and "apt-get" but nothing helped as of now.

Can anybody point me in the right direction?


Thanks

Joerg

---

