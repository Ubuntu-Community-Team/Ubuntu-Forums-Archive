---
title: "Upgrade help needed"
date: 2007-10-03
forum: Installation &amp; Upgrades
---

### Post by abba567 on 2007-10-03
I have 6.06 installed on my laptop and want to upgrade to the latest version, only problem is i cant burn cds is there another way i can do it?

---

### Post by gautada on 2007-10-03
You can always do it via the [network]("http://www.howtogeek.com/howto/ubuntu/upgrade-ubuntu-edgy-to-feisty/").

---

### Post by gautada on 2007-10-03
If you have to have the CDs you can get them [here]("http://www.ubuntu.com/getubuntu").

---

### Post by zvacet on 2007-10-03
Upgrade is going like this Dapper>Edgy>Feisty>Gutsy.Maybe is best to wait few weeks and order new version of Ubuntu.
[http://www.ubuntu.com/getubuntu/shipit-faq]("http://www.ubuntu.com/getubuntu/shipit-faq")

But,if you want to upgrade from net 

dapper>edgy

```
gksu "update-manager -c"
```

when it is finish 

```
sudo sed -e 's/\sdapper/ edgy/g' -i /etc/apt/sources.list
```

```
sudo aptitude update && sudo aptitude upgrade
```

edgy>feisty

[http://www.ubuntu.com/getubuntu/upgrading]("http://www.ubuntu.com/getubuntu/upgrading")

```
sudo sed -e 's/\sedgy/ feisty/g' -i /etc/apt/sources.list
```

```
sudo aptitude update && sudo aptitude upgrade
```

---

