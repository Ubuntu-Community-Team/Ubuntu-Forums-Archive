---
title: "Cannot &quot;apt-get install&quot; in ubuntu 12.04"
date: 2013-03-02
forum: Installation &amp; Upgrades
---

### Post by raksha on 2013-03-02
Hi,
apt get is complete not working for me in ubuntu 12.04
i get the error messenger
 error al procesar /var/cache/apt/archives/autogen_1%3a5.12-0.1ubuntu1_i386.deb (--unpack)

I tried with apt-get clean, autoclean, apt-get -f,...

but anything woorks, the problem is independent of what i try to install:confused::confused:
Could somebody help me?
Thanks a lot

---

### Post by dabl on 2013-03-02
```
sudo rm /var/cache/apt/archives/autogen_1%3a5.12-0.1ubuntu1_i386.deb
```

```
sudo dpkg --configure -a
```

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

---

