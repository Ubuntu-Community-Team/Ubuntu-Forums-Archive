---
title: "Upgradint to 8.10 and keeping all my files"
date: 2008-10-15
forum: Installation &amp; Upgrades
---

### Post by Antihero20 on 2008-10-15
I want to upgrade to Ubuntu 8.10 once its out but i want to keep all my files(videos, music, photos,etc) can this be done? if so then how?

---

### Post by Elfy on 2008-10-15
If you are upgrading then your files won't be touched, if however you need to do a clean install then you will need a seperate /home partition.

If when you installed originally you provided a seperate partition for your /home then when the time comes to reinstall you manually partition and don't format that partition.

If you don't havea seperate partition it is possible to migrate to a seperate one.

If you aren't sure, post the result of 
```
sudo fdisk -l
df -h
``` and we can see from there if it's likely that you have one.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Noea on 2008-10-15
id upgrade to 8.10 and besides problem with rarian pkg and reinstal gnome enviroment nothing was touched . My files was keeped , the program configuration too.

---

