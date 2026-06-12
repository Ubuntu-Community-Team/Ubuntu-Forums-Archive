---
title: "Wine-Gecko?"
date: 2008-06-29
forum: Installation &amp; Upgrades
---

### Post by Jaiibee on 2008-06-29
Hey guys.

Ok, I need to install Wine-Gecko or something, im not sure if this is the right forum.
I have the .cab file, now how the heck to I do whatever with it??

Thnx.

---

### Post by Partyboi2 on 2008-06-29
You should be able to install it by opening a terminal and typing
```
wine iexplore [http://www.winehq.org]("http://www.winehq.org/")
```
> 
Wine Gecko is installed the first time an application tries to use a component of Internet Explorer (eg those found on the [MozillaIntegration]("http://wiki.winehq.org/MozillaIntegration") page) or when the user runs wine iexplore.  If Wine cannot find the necessary files to support Gecko, it will attempt to download them automatically

---

### Post by dualslash on 2008-07-02
When i try to run "wine iexplore" i am never prompted to install gecko. So does that mean it was already installed? Also all I get is a blank screen that says HTML can't be read.

---

### Post by Partyboi2 on 2008-07-02
Have a look at [[COLOR=Blue]this thread[/COLOR]]("http://ubuntu-forum.com/showthread.php?t=332962") or you could try
```
mv /home/[COLOR=Red]username[/COLOR]/.wine /home/[COLOR=Red]username[/COLOR]/.wine.bak
```***Change username to your username, then try
```
wine iexplore http://www.winehq.org
```

---

