---
title: "No Gnome session option in GDM on update"
date: 2008-10-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jonger on 2008-10-12
Hello,
I updated and lost the Gnome session option in GDM.I reinstalled the GDM package but no luck. I can't imagine it being too difficult to fix manually, but i just don't know how to. Thanks,

Jon

---

### Post by plun on 2008-10-12
This one was a little tricky...

I am "trapped" to a Windows PC for the moment so I havent verified it.  

[http://ubuntuforums.org/archive/index.php/t-2920.html](http://ubuntuforums.org/archive/index.php/t-2920.html)

Maybe easier, what gives this ?

```
sudo apt-get update

sudo apt-get upgrade

sudo apt-get install ubuntu-desktop

```

---

### Post by wgrant on 2008-10-12
Ensure that both ubuntu-desktop and xserver-xorg-input-all are installed. We uploaded a transition on Friday night which would have caused apt to want to remove most of GNOME for a few hours.

---

### Post by jonger on 2008-10-12
so i need to make a gnome.desktop file with the following

```
[Desktop Entry]
Encoding=UTF-8
Name=My new Gnome Session
Exec=start*gnome*
Icon=
Type=Application
```

i'm not sure what exec needs to be run.

can any one check their file in
\usr\share\xsession\  *whatever the gnome.desktop file is called

---

### Post by wgrant on 2008-10-12
> **jonger said:**
> so i need to make a gnome.desktop file with the following

[snip]

i'm not sure what exec needs to be run.

can any one check their file in
\usr\share\xsession\  *whatever the gnome.desktop file is called

Try installing ubuntu-desktop before doing this - you should never need to.

---

