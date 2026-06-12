---
title: "uninstalling Mplayer"
date: 2005-05-20
forum: Installation &amp; Upgrades
---

### Post by Pitbull11188 on 2005-05-20
Could someone please tell me how to uninstall Mplayer and its Mozilla plugin because I prefer VLC and I can't get its mozilla plugin to work while the mplayer one is still there. Thanks

---

### Post by mtron on 2005-05-20
what kind of install do you have? 

install via debs:
open  synaptic search for mplayer in the results right click and mark for complete removal

self compiled install:
download the source again unpack in a working directory, usual install way
configure
make

and: **make uninstall**

thats it.

---

### Post by apollyonis on 2005-05-20
Go to System -> Administration -> Synaptic Package Manager -> type in password -> click Search on top right -> type in Mplayer, press enter -> right click mozilla-mplayer -> select Mark for Removal (Do the same for mplayer-386 / 586 / x version as well if you really want to get rid of Mplayer) -> click Apply on top menu bar -> click Apply on confirmation window. Viola! Its done.

---

### Post by Pitbull11188 on 2005-05-20
Thankyou very much but could someone please tell me how to do it via the terminal. I am trying to avoid using synaptic and other gui's because I'm new to linux and would like to learn the Terminal the best I can. Thankyou again.

---

### Post by apollyonis on 2005-05-20
Oh, easy enough. In terminal, type : 

```
sudo dpkg -r mozilla-mplayer
```

I don't know which version of Mplayer you have installed, so just replace the suffix of 386 with 586, or 686 or ppc....whatever you have installed in the following : 

```
sudo dpkg -r mplayer-386
```

Just make sure Synaptic isn't open when you're trying to do this because it will lock up the database and not allow you to uninstall it. If you want to learn terminal commands, just typing the command itself will usually list what it can do I.E. dpkg -r removes debian packages. The command 

```
man dpkg
```

Pulls up a manual over dpkg and shows examples and its usage.

Forgot to add, but if you want a GUI man page view, just go to help and Man Pages from there.  :)

---

