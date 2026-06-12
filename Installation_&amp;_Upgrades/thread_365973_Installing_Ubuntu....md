---
title: "Installing Ubuntu..."
date: 2007-02-20
forum: Installation &amp; Upgrades
---

### Post by Ceco85 on 2007-02-20
While installing Ubuntu can i select which packages to install? I don't want Ubuntu to install the entire CD automatically! Thank you.

---

### Post by taurus on 2007-02-20
I don't think you can select what you want to install and what you don't want to install.  If you don't want to use the default, then install the server version and then install whatever else you want after that with apt-get/aptitude.

---

### Post by Ceco85 on 2007-02-20
Bad news. It's better to have more freedom to select packages by your needs, not to use the default.

---

### Post by taurus on 2007-02-20
And that's what the server version is for.  It will install minimal and you can install whatever else you want after that.

---

### Post by marianlibrarian on 2007-02-20
I have just installed the ubuntu 6.06 server. I now have a lovely command line waiting for me to tell it the next thing to do. Whee! Is it possible to "install" the user interface that comes with the desk top on the server?

---

### Post by taurus on 2007-02-20
> **marianlibrarian said:**
> I have just installed the ubuntu 6.06 server. I now have a lovely command line waiting for me to tell it the next thing to do. Whee! Is it possible to "install" the user interface that comes with the desk top on the server?

At the prompt, do

```
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm start
```

---

### Post by marianlibrarian on 2007-02-20
Thanks! I am installing right now. Looks like it will take about 2 hours. I am using the commands that you (taurus) listed.

I also found this thread, which is a little different but may be helpful. 
[http://www.ubuntuforums.org/showthread.php?t=365195&highlight=desktop+server](http://www.ubuntuforums.org/showthread.php?t=365195&highlight=desktop+server)

---

