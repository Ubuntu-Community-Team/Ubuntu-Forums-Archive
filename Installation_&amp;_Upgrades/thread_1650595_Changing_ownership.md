---
title: "Changing ownership"
date: 2010-12-21
forum: Installation &amp; Upgrades
---

### Post by Speedwagon on 2010-12-21
I'm not quite sure how I managed this, but somehow during a reinstall I changed the ownership of all my home stuff to root, instead of my normal username.  So now nothing loads, unless I sudo it.  I had to use sudo just to open firefox.  How do I fix this?

---

### Post by slooow on 2010-12-21
```
sudo chown -R username.usergroup /home/username
```

---

### Post by Speedwagon on 2010-12-21
I got this:

chown: cannot access `/home/mitch/.gvfs': Permission denied

More details:  I reinstalled 10.10, clean.  I made a backup of my /home directory, and gave it its own drive upon reinstall.  Once I was up and running, I copied from the backup drive to the new /home folder.  I seem to have done something I shouldn't have in this process.

---

### Post by slooow on 2010-12-22
The .gvfs permission denied is a common problem. You can ignore that.

---

