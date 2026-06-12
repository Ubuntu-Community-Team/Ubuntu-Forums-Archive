---
title: "How/when is snaptic package manager updated with latest packages?"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by Andre-D on 2008-05-10
I would like latest Wine. I found some instruction, But I do not know how to use them with GUI (in order to undo them in case of somethig)

I also found that Conduit has a newer version, but not thru the packet manager.

How/when is the packet manager updated ? - how can I apply these instructions ([http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)) to the "software sources" GUI ?

thanks.

---

### Post by kerry_s on 2008-05-10
ubuntu is a snapshot distro, you only get security updates, it's never up to date, by the time it's released it's already at least 3 months old. to be up to date you want to go with a rolling release distro.

also remember newer does not always mean better.

---

### Post by Andre-D on 2008-05-10
Sure . I also agree that newest is not always best.
So the synaptic manager is maintained by Ubuntu, not the all open-source contributors directly.

Thank you.

---

### Post by kerry_s on 2008-05-10
> **Andre-D said:**
> Sure . I also agree that newest is not always best.
So the synaptic manager is maintained by Ubuntu, not the all open-source contributors directly.

Thank you.

ubuntu is built on debian sid(aka:unstable) they grab a copy of the repo(aka:snapshot) and they build ubuntu from there, remaking everything till it's how they want it. it's only updated with security updates after it's released. new programs would be in the next release, because by the time they take there next copy things have already moved along.

now with a rolling release you just update normally new programs are always put in the repo's.
example:
i use debian lenny(testing), after the most of the bugs are worked out in sid(unstable), the programs move to testing.
i just use synaptic or apt-get and update normally. thus keeping my programs newer.

---

### Post by Cifra on 2008-05-10
Let me explain: Synaptic is just a frontend, an interface for APT. It is not affiliated in any way with Ubunt uor Canonical, it is a part of teh GNOME project and it comes with Ubuntu because tehy package GNOME by default.

You get your software from different software repositories - the ones used in ubuntu are in your /etc/apt/sources.list file. They are the safest to use because the software has been tested and used on Ubuntu.

You can also add new repositories, in your own case I'd go to winehq.org and see what their repository address (ask someone on teh forums or google it) is and add it to my sources.list file the run "apt-get update" and there you have it, the newest WINE should be there :)

Tell me if you need more help or is this enough information for you :)

oh and read this:
[http://linux.about.com/od/xubuntu_doc/a/xubudg13t04.htm](http://linux.about.com/od/xubuntu_doc/a/xubudg13t04.htm)

---

### Post by kerry_s on 2008-05-10
can you post the wine repo for him?
maybe a list of repos usable with his ubuntu version?

---

### Post by Pumalite on 2008-05-10
What is his version?

---

### Post by Andre-D on 2008-05-10
Thanks to all.

I like Ubuntu, I am an IT-professional, but rather new to Linux.

"What is my version?" - I assume you mean Ubuntu - 8.04
I would be helped if somebody told me how to translate the information listed here: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)  -for use in the GUI

The reason for me to wish to add it in GUI (application: "Software Sources", tab: "third-party software")
instead, is to easily remove it /see the changes I've made, - (but I really think I am able to do it in terminal as well - just don't know how.)

---

### Post by Pumalite on 2008-05-10
In the Terminal:
wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list](http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/winehq.list
sudo apt-get update

---

