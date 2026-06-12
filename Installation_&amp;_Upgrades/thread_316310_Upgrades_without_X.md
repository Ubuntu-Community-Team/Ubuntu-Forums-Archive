---
title: "Upgrades without X"
date: 2006-12-10
forum: Installation &amp; Upgrades
---

### Post by WonderClown on 2006-12-10
OK, I've searched the forums here and found a few posts asking this question, but I haven't found a thread where any of the ubuntu developers actually gave an answer.  Forgive me if I'm beating a dead horse.

Is there any "supported" mechanism of updating an ubuntu system that does not have the X client libraries installed, and therefore cannot run update-manager?  The systems I run ubuntu on are headless boxes out on the network, which I access only via ssh and I do NOT wish to install all of the X libs and gtk and everything required to make update-manager run.

It seems to me that most of the complaints about the dapper->edgy upgrade seem to be related to X, so perhaps I will be OK just doing an apt-get dist-upgrade?  Can anybody tell me whether this is supported or not, or what other things I might have to clean up afterward?  TIA.

---

### Post by riven0 on 2006-12-10
Are you saying your running a server box, (without any graphics), and you want to update? In that case, just go ahead and do:

> sudo apt-get update && sudo apt-get dist-upgrade

As long as you don't have xserver installed, Ubuntu won't try to install it for you.

---

### Post by WonderClown on 2006-12-10
But I've read a lot of horror stories about doing the Dapper->Edgy update without using update-manager.  In fact, one of the sticky posts at the top of this forum is a dire warning against using apt-get to upgrade to edgy.  The official Edgy upgrade instructions on the wiki ([https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)) specifically say that using apt-get is less reliable than using update-manager, and will likely result in stuff that has to be cleaned up afterward.  Given that these are  remote boxes and I don't have easy console access in case things get really broken, I'm feeling pretty "edgy" about the Edgy upgrade.

---

### Post by riven0 on 2006-12-10
Oh, I get what your saying now. You want to go from Dapper to Edgy without upgraded the xserver. 

Well, first, just doing a **sudo apt-get dist-upgrade** will not upgrade to Edgy, it will just update your current Dapper installation. 

If you want to upgrade to Edgy, I don't know of any way to tell the update-manager that you don't want the X upgraded. It will do it automatically. Once you run **gksu "update-manager -c"** thats it, it upgrades everything.

---

### Post by WonderClown on 2006-12-10
I am not worried about update-manager upgrading X.  My problem is that I cannot even install update-manager without having X installed.  update-manager is a GTK+ app (I think?), and so it has to have all the X client libraries (not the server) installed, and all the gtk libraries, and maybe even the gnome libraries.  I specifically do not want all that crap installed on these servers, just so that I can do an upgrade.  So installing update-manager is not an option.  I know that I can edit /etc/apt/sources.list manually, replacing all instances of "dapper" with "edgy", and then use apt-get to do the upgrade, but the upgrade guide for Edgy says this is a bad idea.  My question is -- well, if that's a bad idea, how **should** I do it if I don't have X libraries installed?  And if the answer is "install the X/gtk/gnome libraries just so you can use update-manager", well, I think the Ubuntu developers need to seriously rethink their strategy.  This is still *Linux,* isn't it, so shouldn't I be able to run a server without installing any GUI apps?  Maybe update-manager needs to be split into a text-mode app and a graphical app, which share the same backend logic.  Or else they just need to make upgrades with with apt-get.

---

### Post by Johan! on 2006-12-10
If it's a server, why would you want to upgrade to edgy?

If you really want to switch to edgy, make a backup, and try apt-get.
If it doesn't work, you still have your backup, and you can try something else.

---

### Post by confused57 on 2006-12-10
It would probably be better to stick with Dapper, it's long term support and more stable than Edgy.
If you just want to try it(have nothing to lose), you could:

```
sudo nano /etc/apt/sources.list
```
change all instances of dapper to edgy(might want to put a # in front any cd-rom sources), then:

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

---

