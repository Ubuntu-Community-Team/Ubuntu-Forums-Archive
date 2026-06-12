---
title: "Xubuntu 12.04 without any pre-installed sofware"
date: 2012-05-30
forum: Installation &amp; Upgrades
---

### Post by Denco1 on 2012-05-30
Hello,
I would like to ask, if there is any way of installing Xubuntu 12.10 without any pre-installed software (like Firefox, Abiword, etc.). I know, that I can uninstall it, but I would like to install my own choice of software.
Thanks for your replies.

//Sorry for mistake, I mean 12.04 :lolflag:

---

### Post by wilee-nilee on 2012-05-30
You might checkout the minimal cd, I'm not sure you can break apart a desktop though to install just specific parts. It is a netload and you can get a more minimal set up for sure hence the name.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by Denco1 on 2012-05-30
I got to "command line install" with Minimal CD. But that is too much, I like normal Xubuntu installation except the preinstalled software :rolleyes:

---

### Post by ottosykora on 2012-05-30
> **Denco1 said:**
> I got to "command line install" with Minimal CD. But that is too much, I like normal Xubuntu installation except the preinstalled software :rolleyes:

well it all depends what you understand as preinstalled software.

Xubuntu is linux distribution and it has preinstalled software like xubuntu desktop for example, without this it is not xubuntu.
It needs some basic functions if it should behave like some graphical interface, it needs some file manager, it needs some browser, it needs some kind of package manager, it needs some additional drivers, it needs some kind of terminal software, it needs gpg and associated agents and daemons, it need some desktop drawing program,.....etc etc.
If you leave all the preinstalled programs as you call it away, then you have basic linux kernel to play with.

---

### Post by wilee-nilee on 2012-05-30
> **Denco1 said:**
> I got to "command line install" with Minimal CD. But that is too much, I like normal Xubuntu installation except the preinstalled software :rolleyes:

Understandable, I think though that what you want to do is a customized setup, so getting someone to figure this out then instruct you may be a bit of a wait if at all.

You could try using the IRC  at freenode in the #xubuntu or #ubuntu channel for clues on this.

Honestly I would just install it and remove what you don't want, your wait for help may be long, if you even get help, and I suspect, the closest you can get to what you want is through that minimal cd.

---

### Post by Lyfang on 2012-05-30
A solution would be to create a LiveCD using Remastersys ([http://www.remastersys.com/](http://www.remastersys.com/)). After installing Xubuntu you'll be able to choose which packages to install using e.g. Synaptic. See also: LiveCD Creator ([https://wiki.ubuntu.com/LiveCDCreator](https://wiki.ubuntu.com/LiveCDCreator)) in the future. From my experience a Minimal CD installation took a long, long time to install.

You could create a simple Bash script or copy & paste something like this:

```
sudo apt-get remove firefox abiword && sudo apt-get update && sudo apt-get install PACKAGENAME
```

---

### Post by wilee-nilee on 2012-05-30
> **Lyfang said:**
> A solution would be to create a LiveCD using Remastersys ([http://www.remastersys.com/](http://www.remastersys.com/)). After installing Xubuntu you'll be able to choose which packages to install using e.g. Synaptic. See also: LiveCD Creator ([https://wiki.ubuntu.com/LiveCDCreator](https://wiki.ubuntu.com/LiveCDCreator)) in the future. From my experience a Minimal CD installation took a long, long time to install.

You could create a simple Bash script or copy & paste something like this:

```
sudo apt-get remove firefox abiword && sudo apt-get update && sudo apt-get install PACKAGENAME
```

Good idea I had thought this way as well, I was not sure if the user wants the first install to be missing the not wanted packages or wanted to generate a disc with them missing.

Actually the net instal seems to be a bit longer but palatable, but you have to know how to do it, not difficult but can intimidate some users.

---

### Post by raja.genupula on 2012-05-30
from this you can get the 12.04 with no packages installed and then you can install what apps you want and you can upgrade it too .
Its equals to desktop edition but without any pkgs installed 

[http://www.ubuntu-mini-remix.org/](http://www.ubuntu-mini-remix.org/)

---

### Post by sffvba[e0rt on 2012-05-30
Title of thread updated.


404

---

### Post by Denco1 on 2012-05-31
Thanks, I will check your advices and post back with results.

//Well, at the end I decided to install Xubuntu in usuall way and uninstall what I do not need, thanks for your time.

---

