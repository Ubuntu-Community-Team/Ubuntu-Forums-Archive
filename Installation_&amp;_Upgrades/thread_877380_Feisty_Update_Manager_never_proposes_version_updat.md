---
title: "Feisty Update Manager never proposes version updates..."
date: 2008-08-01
forum: Installation &amp; Upgrades
---

### Post by charriso on 2008-08-01
Hi,

The title says it all really. I'm running 7.04 (Feisty) in Parallels Desktop on a Mac (Intel), and although I regularly get app/system updates from the Update Manager, I have never had a version update proposed, (which is why I'm still with 7.04).

What might I tweak to overcome this? 

Many thanks.

---

### Post by Pumalite on 2008-08-01
Have your Feisty fully updated and remove all third parties from your sources.list. Then you can try:
sudo sed -i 's/feisty/gutsy/' /etc/apt/sources.list 

sudo apt-get update 

sudo apt-get dist-upgrade

---

### Post by zvacet on 2008-08-01
**system>admin<software sources>upgrades**>at the bottom you will see **release upgrade** option and there select which one you want to be prompted for.

---

### Post by omar1987 on 2008-11-03
i need this thing withoud paying :d

---

### Post by Pumalite on 2008-11-03
Don't forget to remove your Medibuntu folder also (if you have it)

---

