---
title: "Please help : major upgrade problems"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by nimonika on 2010-10-12
The update manager has suddenly stopped doing updates. I attached here a link to the screenshot of the error messages. Please could someone help me debug 

[http://www.cs.le.ac.uk/people/ms491/error.png](http://www.cs.le.ac.uk/people/ms491/error.png)

Many thanks

---

### Post by lechien73 on 2010-10-12
It looks like some of your .list files have got corrupted.

You could try the following to recover:

```
cd /var/lib/dpkg/info
sudo rm python-appindicator.list
sudo apt-get --reinstall install python-appindicator

```
You might have to do this for the other files (libgtk2.0-bin etc) as well.

---

