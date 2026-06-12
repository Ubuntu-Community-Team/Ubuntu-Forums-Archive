---
title: "Second Stage Installation problem?"
date: 2005-07-24
forum: Installation &amp; Upgrades
---

### Post by sra136 on 2005-07-24
I passed the first stage of the installation.  However, sometime during Second stage,  automatic package installation did not pass, and was asked to manually install.  However, i did not know what i did and now when i boot, ubuntu is loaded, linux is uncompressed, but i am at a command prompt asking for Username and Password.  I log in and am still at the command prompt.  I feel as though only the kernel was installed without anything else?

---

### Post by neltnerb on 2005-07-24
The first thing I would try is typing

```
sudo gdm
```

If it installed x-windows, this command should start the gnome window manager.

If that doesn't work, I'd suggest doing

```
apt-get -f install
```

to see if that restarts the package installation.

If that fails, try

```
apt-get install gnome
```

That should tell it to install gnome...

Perhaps your network isn't configured correctly there and it couldnt' download packages?

---

### Post by sra136 on 2005-07-24
i did a refresh install.  However, some packages did not install and I am once again at Aptitude like last time.  But i want to get it right.  Dont know where to begin with Aptitude.  Help?

By the way, this is Kubuntu that is installed on my machine?

---

