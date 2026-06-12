---
title: "Installing Django"
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by duane9 on 2010-06-07
I upgraded to ubuntu 10.04. It didn't have the latest version of Django. So I downloaded it and installed it in the terminal with **sudo python setup.py install**. It installed, and I've been using it. It works great. The only problem is, I don't know where Django installed. I look in /usr/local/lib/python2.6/site-packages/ and there is nothing there. Where is it?

---

### Post by SlidingHorn on 2010-06-07
Try looking in /var/lib/python-support/python2.5/django

Source: [http://ubuntuforums.org/showpost.php?p=4533643&postcount=3](http://ubuntuforums.org/showpost.php?p=4533643&postcount=3)

---

### Post by duane9 on 2010-06-07
It's not there either.

---

### Post by duane9 on 2010-06-07
Found it. Don't know why it's here, but here is where it is:
/usr/local/lib/python2.6/dist-packages/django

---

