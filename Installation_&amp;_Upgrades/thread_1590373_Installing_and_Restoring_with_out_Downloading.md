---
title: "Installing and Restoring with out Downloading"
date: 2010-10-07
forum: Installation &amp; Upgrades
---

### Post by Jonny87 on 2010-10-07
I'm wanting to do a clean install but with a slow Internet connection it will take for ever to update and re-install my software from the Internet.

Is there an easy way that I can use the packages that are saved in /var/cache/apt/archives with out hitting dependancy and version issues?

---

### Post by mikewhatever on 2010-10-07
If you don't have Ubuntu installed, where would you get these packages from? You haven't mentioned another computer, so I assume there is none.

---

### Post by sikander3786 on 2010-10-07
> **mikewhatever said:**
> If you don't have Ubuntu installed, where would you get these packages from? You haven't mentioned another computer, so I assume there is none.
I think he means he wants to do a fresh install with Ubuntu.

You can save all your existing packages using APTonCD and reinstall them later.

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by Jonny87 on 2010-10-07
> **mikewhatever said:**
> If you don't have Ubuntu installed, where would you get these packages from? You haven't mentioned another computer, so I assume there is none.

Sorry should have mentioned that its a Re-install. I currently have Kubuntu but I want to go back to standard Ubuntu. I thinking about saving the packages in /var/cache/apt/archives using them some how to reinstall the software that I want, Plus I have a laptop with the an upto date version of Ubuntu 10:04 that I could use to source packages from.

I have a CD to Install from, its just a matter of getting it up to date and with the extra software with as little download as possible

---

### Post by sikander3786 on 2010-10-07
> I currently have Kubuntu but I want to go back to standard Ubuntu.

You can install GNOME on Kubuntu thus making it standard Ubuntu without the need of re installation. You can switch between GNOME and KDE at the login screen.

```
sudo apt-get install ubuntu-desktop
```

---

### Post by Jonny87 on 2010-10-07
> **sikander3786 said:**
> You can install GNOME on Kubuntu thus making it standard Ubuntu without the need of re installation. You can switch between GNOME and KDE at the login screen.

```
sudo apt-get install ubuntu-desktop
```

Yea thats basically the setup that I have at the moment but I want to get rid of Kubuntu all together as I don't need it. Hence wanting to do a clean install.

I see that APTonCD creates an ISO, can I install packages straight from that ISO or does it have to be on CD?

---

### Post by sikander3786 on 2010-10-07
I am not that much experienced with it. Never needed because I have got a 8 MBPs connection. `More information here,

[http://aptoncd.sourceforge.net/doc-manual.html](http://aptoncd.sourceforge.net/doc-manual.html)

---

### Post by Jonny87 on 2010-10-08
Well it worked but not perfectly. when I accesed it from synaptic it told me that that some of the packages were already installed.

---

### Post by iiiears on 2010-10-08
Apt on CD - nice tip.

Try asking synaptic to only create a download package list then use dpkg -i * after collecting the packages you have into directories by task. /ubuntu-reinstall, /mp3-encoding /programming-svn-git /vmware etc

---

