---
title: "Update 5.04 -&gt; 5.10"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by XorpiZ on 2005-10-13
Hi everybody.. First post, so bear with me if it's placed the wrong place :) 

So, I've just installed Hoary Hedgehog a few days ago, and I would be sad to reinstall everything to get Breezy Badger.. Is there anyway to upgrade without reinstalling?

Thanks in advance!

---

### Post by SilverTab on 2005-10-13
Open your sources.list  (sudo gedit /etc/apt/sources.list )

do a find and replace...replace "hoary" with "breezy"
save the file...

now open a terminal...
sudo apt-get update
sudo apt-get dist-upgrade

it will take a while....really...a whiiiile

---

### Post by XorpiZ on 2005-10-13
Thanks. Seems to be working like a charm :)

---

