---
title: "Login/Logout after upgrade to 7.10"
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by gamgee911 on 2007-11-02
After upgrading my PowerBook (ppc) from 7.04 to 7.10, I am now missing the splash that comes up after I login and I am missing the sound after I logout.  Everything else works fine, is there a way to bring back these things?  Thanks

---

### Post by por100pre1 on 2007-11-03
Not sure if this will help, but try this:

```
sudo cp /etc/usplash.conf /etc/usplash.conf_backup
```

```
gksudo gedit /etc/usplash.conf
```

Something like this should appear:

> # Usplash configuration file
xres=1024
yres=768

Change the resolution and save.

If that is not enough try [this]("http://ubuntuforums.org/showpost.php?p=3676690&postcount=2").

---

### Post by gamgee911 on 2007-11-05
Just any resolution?  600 x 800 for example?

---

### Post by por100pre1 on 2007-11-06
> **gamgee911 said:**
> Just any resolution?  600 x 800 for example?

Your current system resolution actually. If that doesn't work, please check [this]("http://ubuntuforums.org/showpost.php?p=3676690&postcount=2").

EDIT: 600 x 800 is not a resolution. It should be 800 x 600 for example.

---

