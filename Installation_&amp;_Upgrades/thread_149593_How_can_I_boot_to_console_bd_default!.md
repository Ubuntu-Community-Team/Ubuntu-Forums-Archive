---
title: "How can I boot to console bd default!"
date: 2006-03-24
forum: Installation &amp; Upgrades
---

### Post by chugru on 2006-03-24
Hi, All...

Kubuntu, by default, boots into it's DM (KDE) using kdm. I would prefer for it to boot to console and allow me to log into my user account and start KDE, by choice, using the **startx** command.

Would someone please tell me the modifications I must make to implement such a change?

Thanks!

---

### Post by Sef on 2006-03-27
At the start up menu (where you enter your name and password), just click on sessions and that is one of the options.

---

### Post by Ensnared on 2006-03-27
What you need to do is disable the automatic startup of GDM or KDM (whichever one you use) at startup.

If you're in X you can just run the service configuration tool (services-admin, located under System->Administration->Services in Gnome) and uncheck the box for KDM or GDM.

If you're using the command line you need to edit the symlinks controlling the given runlevel. On Ubuntu the default runlevel is 2, which means the symlinks are located in /etc/rc2.d. Maybe Ubuntu has some command line utility that makes this simpler, but I don't know what it's called.

If you're using KDM:
```
cd /etc/rc2.d
mv S99kdm K01kdm
```

If you're using GDM:
```
cd /etc/rc2.d
mv S13gdm K01gdm
```
The numbers might be different for you (I think my system has the default values though), but the point is that everything in this dir named "SXXsomething" will start in this runlevel (with priority XX - higher being later in the boot-process), while everything named "KXXsomething" will be stopped (or not started if it's not running) in this runlevel.

Regardless of which way you do it, this will prevent KDM and/or GDM from starting automatically when you boot your computer, and you'll start X by issuing "startx" instead.

---

### Post by ibanez88 on 2006-04-28
I'd like to not use kdm either... is there any danger in simply doing a 
sudo apt-get remove kdm 
?

---

### Post by Ensnared on 2006-04-28
[QUOTE=ibanez88]I'd like to not use kdm either... is there any danger in simply doing a 
sudo apt-get remove kdm?[/QUOTE]
Shouldn't be a problem. It will remove some dependencies like kubuntu-desktop - but that's not an actual package anyway - and any kdm-themes package you've installed, but it shouldn't remove anything that will break KDE itself.

---

