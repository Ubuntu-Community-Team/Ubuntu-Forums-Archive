---
title: "Kubuntu and Gnome on same laptop"
date: 2007-02-13
forum: Installation &amp; Upgrades
---

### Post by scottsanpedro on 2007-02-13
Hi,
Just install Kubuntu oem on my laptop.
Then ran 
```

sudo aptitude install gnome-desktop

```

when I restart I don;t get the option to change envoironments??
Anyway I can do this?
Many thanks
Scott

---

### Post by mithras86 on 2007-02-13
In your KDM (your login screen) there is the possibility to choose between different startup options. You can get X, KDE or a Gnome session. I thought this options are called 'session'.
Googled on kdm, i found [this]("http://whoiam55.at.preempted.net/images/installing_kubuntu/kdm.jpg") image, showing a 'session type' option. There can you change it.

---

### Post by kebes on 2007-02-13
Your login screen might also look like this:
[http://www.kubuntu.org/docs/images/C/kubuntu-login.png](http://www.kubuntu.org/docs/images/C/kubuntu-login.png)

it's the same thing, though... click on the left-most icon ("session type") and in the list both KDE (probably the default) and Gnome should be listed. So you can switch it there.

---

### Post by scottsanpedro on 2007-02-13
maybe I have a different version. It looks little a computer tower. When clicked it shows a selection for session.
It only shows 
default(previous)
KDE
failsafe

Have I not installed gnome correctly?

Thanks for quick response

---

### Post by kebes on 2007-02-13
You said you installed "[gnome-desktop]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gnome-desktop&searchon=names&subword=1&version=all&release=all")", but I think you actually need to install the meta-package "[ubuntu-desktop]("http://packages.ubuntu.com/edgy/metapackages/ubuntu-desktop")" (which installs gnome and then adds Ubuntu-specific gnome-related things, too).

If you did indeed install gnome-desktop, I think it's safe to just install ubuntu-desktop (most of its dependencies will already be installed, obviously). I think this package makes the change to the login manager.

---

### Post by scottsanpedro on 2007-02-13
many thanks. will give it a try and finsh off the thread. Thanks

---

### Post by mithras86 on 2007-02-14
Sorry, what kebes says is correct. Though you have already gnome, installing ubuntu-dekstop will install your whole gnome environment. Then ubuntu knows you have gnome and you can start gnome with a session ;)

---

