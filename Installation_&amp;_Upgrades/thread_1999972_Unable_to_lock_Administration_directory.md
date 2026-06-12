---
title: "Unable to lock Administration directory"
date: 2012-06-08
forum: Installation &amp; Upgrades
---

### Post by reaxas on 2012-06-08
I've seen other people with this problem, but I'm still not sure how to solve it.

I'm trying to install User-Theme GNOME Shell Extension and I keep getting the error: 
" E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"

I've tried to kill the program and such and nothing has worked out yet, if anyone can help me, it'll be much appreciated!

Thanks in advance!

---

### Post by Old_Grey_Wolf on 2012-06-09
You need to remove the lock file. Enter these commands to do that ```
sudo rm /var/lib/dpkg/lock
sudo dpkg --configure -a
```

---

### Post by reaxas on 2012-06-10
> **Old_Gray_Wolf said:**
> You need to remove the lock file. Enter these commands to do that ```
sudo rm /var/lib/dpkg/lock
sudo dpkg --configure -a
```

It worked like a charm! Thank you so much!

---

### Post by Old_Grey_Wolf on 2012-06-10
Please mark this thread as solved.

If you do not know how to do that, near the top of the webpage (scroll up) there is a menu "Thread Tools". Select "Mark this thread as solved". It lets other people searching the forums know that this had a working solution and they don't need to provide additional help.

Thank you.

---

