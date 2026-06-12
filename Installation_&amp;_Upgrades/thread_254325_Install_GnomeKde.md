---
title: "Install Gnome/Kde"
date: 2006-09-09
forum: Installation &amp; Upgrades
---

### Post by BruceWilkinson on 2006-09-09
On startup all I have is a command line interface after installing server 6.06.1. I'd like to have a GUI for the primary interface and use CLI when I choose to. So I tried to install Gnome using: sudo apt-get install gnome, and I get:

Building package lists... Done
Building dependency tree... Done
Package gnome is not available, but is referred to by another package.
This may mean that the package is missing, or has been obsoleted, or is
only available from another source.
E: Package gnome has no installation candidate.

I get the same error if I try to install kde: sudo apt-get install kde.

How do I install either or both packages in Ubuntu?

Just for reference, one of the reasons I tried Ubuntu was because it has a reputation for being easy to use. Easy must be a relative term. For someone with Red Hat and Xandros experience, Ubuntu doesn't qualify as easy.

Bruce

---

### Post by meng on 2006-09-09
Comment noted. Sorry you're finding it so difficult, perhaps Red Hat and/or Xandros just suit you better. As someone who has tried Red Hat before, I found Ubuntu much easier. Just goes to show that tastes vary.
The usual way to install GNOME or KDE is:
sudo apt-get install ubuntu-desktop
sudo apt-get install kubuntu-desktop
this includes a bunch of GNOME and KDE apps considered "standard fare".

---

### Post by aysiu on 2006-09-10
You're complaining about not having a GUI after installing the *server* edition?

The server edition is for servers.

If you want a GUI, get the Desktop CD or the Alternate CD.

That said, you can install Gnome or KDE with the commands meng gave you.

---

### Post by kelean on 2006-09-10
If you installed the server edition then X is not installed as far as i know.  So if you want to install Gnome or Kde desktop you would need to install first

---

### Post by BruceWilkinson on 2006-09-13
First off, sorry for disparaging Ubuntu. I didn't mean to offend and should have kept my mouth shut. I let frustration out, sorry.

Second, thanks meng, aysiu and kelean for your replies. In the Linux server world, desktop's have a gui, servers use a command line. I'll get there. For now, I'm not familiar or skilled enough to go with a gui.

---

### Post by BruceWilkinson on 2006-09-13
Correction, go without a gui. Too many things going on at the same time (and an inherant inability to type!).

---

