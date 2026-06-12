---
title: "Module dav does not exist!"
date: 2010-09-20
forum: Installation &amp; Upgrades
---

### Post by dsailer on 2010-09-20
I had some issues with my apache2 install and didn't really need to save current config so decided to delete and reinstall. Now I'm getting the following when installing libapache2-svn:

```
me:$ sudo apt-get install libapache2-svn
Reading package lists... Done
etc, etc
Considering dependency dav for dav_svn:
ERROR: Module dav does not exist!
```

I've tried deleting apache2, svn and libapache2-svn and reinstalling but still get the error.

---

### Post by dsailer on 2010-09-21
in fact I get this error on ANY installs I try to do with apt-get.

any ideas?

---

### Post by dsailer on 2010-09-22
bump...

I'm willing to try about anything at this point. Next step, clean install of Ubuntu.

---

### Post by dsailer on 2010-09-22
this post helped me out:

[http://ubuntuforums.org/archive/index.php/t-471003.html](http://ubuntuforums.org/archive/index.php/t-471003.html)

---

