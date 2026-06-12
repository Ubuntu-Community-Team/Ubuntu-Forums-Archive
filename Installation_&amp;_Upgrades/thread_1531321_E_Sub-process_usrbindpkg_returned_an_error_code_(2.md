---
title: "E: Sub-process /usr/bin/dpkg returned an error code (2) after sudo apt-get dist-upgra"
date: 2010-07-14
forum: Installation &amp; Upgrades
---

### Post by l0uismustdie on 2010-07-14
I recently installed Ubuntu 9.10 off a USB key.  Directly afterwords I ran 
```

sudo apt-get update
sudo apt-get dist-upgrade

```because I thought this would do the upgrade to 10.04.  This seems to updating a lot of my packages but not the actual kernel.

Following this I tried to run the update from the Update Manager with no luck either.  It essentially kept giving me an error saying my packages were already updated.
Now when I try 
```

sudo apt-get dist-upgrade

```I get the error
```

E: Sub-process /usr/bin/dpkg returned an error code (2)

```Anyone have any idea what is exactly going on here?

---

### Post by oldos2er on 2010-07-14
If you want to upgrade to 10.04, run ```
update-manager -d
```

---

