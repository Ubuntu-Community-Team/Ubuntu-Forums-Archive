---
title: "help!! how to enable gd in php?"
date: 2005-03-05
forum: Installation &amp; Upgrades
---

### Post by isaac on 2005-03-05
i'm very eager to use image drawing command in php but it seems that the apt-get php4 did not get the gd enable...

it seems like i need to enable it by adding "--with-gd" in the configure parameter... but where is the configure parameter located??!?!?!

---

### Post by alastair on 2005-03-05
There's a GD package separate eg.

php4-gd
php4-gd2

I found this by typing :

apt-cache search php | grep gd

Try installing the relevant php GD package.

---

