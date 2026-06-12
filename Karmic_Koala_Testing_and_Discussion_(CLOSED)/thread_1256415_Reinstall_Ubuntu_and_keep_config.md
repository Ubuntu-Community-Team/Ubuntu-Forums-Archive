---
title: "Reinstall Ubuntu and keep config"
date: 2009-09-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Luca_turicci on 2009-09-02
Hi you all, as we all know, the next Alpha of karmic is right around the corner, and i'm really looking forward to do a fresh install of it, BUT, i don't want to loose my desktop config (screenlets, wallpaper, skins, icons, etc.) and the apps i've installed.

I've read about backing up the /home folder, could that be the way to keep my config and apps? plus, i don't want to keep the looooooooong list of kernels in GRUB2 and neither want grub to ask me wich kernel to boot everytime, any help?

---

### Post by Luca_turicci on 2009-09-02
BUMP

Really need help, new Alpha comes out tomorrow!!!!!!!

---

### Post by raymondh on 2009-09-02
> **Luca_turicci said:**
> BUMP

Really need help, new Alpha comes out tomorrow!!!!!!!

Luca_turicci,

I have used [apton CD]("http://aptoncd.sourceforge.net/") to move apps (just apps) from jaunty to jaunty.  I have never used it to move from Jaunty to Karmic.

You may want to try it out.  If so, post back results.

Good luck.

---

### Post by miklcct on 2009-09-03
/etc = system configuration files
~username/.[!.]* = user configuration files

```

$ aptitude search '~i!~M' # All manual packages installed

```

---

### Post by Luca_turicci on 2009-09-03
Great, i didn't understand....  could you please explain a little?

---

### Post by slakkie on 2009-09-03
If you run Karmic already, just remove the old kernels:

```

sudo aptitude purge $(dpkg -l | egrep "linux-(image|headers)" | egrep -v  "$(uname -r | sed -e 's/-generic//' -e 's/-server//' -e 's/-virtual//')|linux-(image|headers)-(generic|server|virtual)" | awk '{print $2}')

```

Then do the normal upgrade:

```

sudo aptitude update && sudo aptitude safe-upgrade

```

Backup your homedir:

```

tar zcvf /path/to/somewhere/home.tgz  $HOME

```

Maybe also backup your /etc dir

```

sudo tar zcvf /path/to/somewhere/etc.tgz  /etc

```
Get a list of all your installed apps:

```

dpkg --get-selections >  /path/to/installed_pkg

```

If you need to reinstall a new box:

```

tar zxvf /path/to/somewhere/home.tgz
sudo tar zxvf /path/to/somewhere/etc.tgz 
sudo dpkg --set-selections < /path/to/installed_pkg
sudo apt-get dselect-upgrade

```

What you can also do is save your homedir and root slice with clonezilla, which works really nice.

---

