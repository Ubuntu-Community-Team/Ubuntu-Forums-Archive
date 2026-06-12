---
title: "How would I..(Ubuntu to Kbuntu)"
date: 2007-07-26
forum: Installation &amp; Upgrades
---

### Post by gamefreak863 on 2007-07-26
how do I take my Ubuntu, and install Kbuntu over it?

I read somewhere how to do it...but I can't find it again.

Any help?

---

### Post by reckless2k2 on 2007-07-26
synaptic and install kubuntu-desktop

---

### Post by davidjmayo on 2007-07-26
see here [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by gamefreak863 on 2007-07-26
ok, but that website said I'd have GNOME programs..and KDE programs...how do I make it...just like a fresh install of KDE...without a cd?

---

### Post by dabl on 2007-07-26
I don't think you can end up gnome-less if you start with Ubuntu.  If you will install the *kubuntu-desktop* metapackage, then you get the KDE desktop environment, which will run under the KDM X server manager, and you can have all the KDE apps you want and it will be the same as a Kubuntu installation.  But, at boot time, you'll have to pick Gnome or KDE as the desktop environment to boot into (so I read -- I didn't do it that way).

Or you can do like me and install one of each on different hard drives.   :popcorn:

---

### Post by gamefreak863 on 2007-07-26
the only thing I'm worried about, if I do it that way....is having GNOME apps squished in with the KDE apps...like that site said would happen...I would install KDE on my external...but I have no cd's

---

### Post by dabl on 2007-07-26
Some gnome packages work fine in Kubuntu -- gnomebaker and Gnome Wave Cleaner are two that I have used.  But, Nautilus and gedit and the major ones that you use in Ubuntu are not available as packages in Kubuntu unless you install a zillion gtk library modules.

---

### Post by davidjmayo on 2007-07-26
look at these and decide if you like it. click on the thumbs for screenshots (It's what I use)

[http://www.kde-look.org/content/show.php?content=31031&forumpage=2](http://www.kde-look.org/content/show.php?content=31031&forumpage=2)
[http://www.gnome-look.org/content/show.php/Gnome+Menu+Extended+%28Debian+Package%29?content=31035&PHPSESSID=6](http://www.gnome-look.org/content/show.php/Gnome+Menu+Extended+%28Debian+Package%29?content=31035&PHPSESSID=6)

---

### Post by Brian96 on 2007-07-26
> **gamefreak863 said:**
> ok, but that website said I'd have GNOME programs..and KDE programs...how do I make it...just like a fresh install of KDE...without a cd?

I don't know that it can be done if you installed using the Ubuntu Live CD (which is the default download from the Ubuntu website).

If you download the Alternate CD you can do a server install and then at the command prompt install kubuntu-desktop. Then if you decide you don't like it you can uninstall it (leaving Ubuntu server intact) and install ubuntu-desktop or kubuntu-desktop. (If you are not sure what I am talking about, you might not want to try this method.)

Anyway, the best way I've found to play around with different desktop environments is to start with a server install, then install and uninstall the different DEs. Adding kubuntu-desktop on top of an ubuntu-desktop install gave me all kinds of crazy programs everywhere. And I never could get kubuntu-desktop cleanly uninstalled from ubuntu-desktop.

---

