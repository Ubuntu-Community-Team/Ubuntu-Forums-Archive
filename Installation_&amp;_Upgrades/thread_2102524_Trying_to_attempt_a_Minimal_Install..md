---
title: "Trying to attempt a Minimal Install."
date: 2013-01-07
forum: Installation &amp; Upgrades
---

### Post by Mocha Fresh on 2013-01-07
Hello Everybody, I've got some questions that I'd like to be answered. I'm trying to preform a minimal install 12.10, because I would like to use Steam for Linux beta. 

I'm aware of how to Install the OS, but if I CLI what should I install to get the full experience without the bloat? "Ubuntu-Desktop" contains the games, office suit, etc.

I would like to have the bootscreen, default looking login and mate rather than unity desktop. 

Thank you for your time. - Mocha

---

### Post by ibjsb4 on 2013-01-07
I don't know about mate, my basic install is gnome.

```
sudo apt-get install lightdm gnome-terminal synaptic && sudo apt-get install --no-install-recommends gnome-session-fallback
```

If you do this you need to fix the panel background color with Alt + Right click to be able to see the menu.  And gnome terminal may also be black on black.

Thats just one of many ways to do this.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=server+gui&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=server+gui&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by snowpine on 2013-01-07
Welcome to the forums! If you are new to Ubuntu then I recommend the default full install. A full install of Ubuntu uses only a few GB of hard drive space. If you have a typical 1TB hard drive then Ubuntu will use less than 1% of it. This is not the definition of "bloat."

If you prefer a minimal install for whatever reason then here is a good how-to: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

(substitute the desktop environment of your choice for icewm)

---

### Post by ibjsb4 on 2013-01-07
Another option to trim down an ubuntu-desktop install using the mini iso would be installing without recommended packages.  This will still give you the Unity desktop.

[http://packages.ubuntu.com/quantal/ubuntu-desktop](http://packages.ubuntu.com/quantal/ubuntu-desktop)

And to do that from the mini iso:

```
sudo apt-get install --no-install-recommends ubuntu-desktop
```

---

