---
title: "How do you install software?"
date: 2007-06-16
forum: Installation &amp; Upgrades
---

### Post by doccpu on 2007-06-16
If you find some cool spftware  like samba, swat or a game, how do you install it? Can you point something to the rpm or whatever file it comes in? ie what if its not listed by ubuntu's upgrade service as available?

---

### Post by kevinlyfellow on 2007-06-17
Most software you get will be available through Synaptic Package Manager.  In this program you can add new repositories (or repos for short) that will make the database even bigger.

If a package can not be found in the repos (another way of saying you can't install it via Synaptic), then you can download a debian installation file (*.deb).  You can either install it via commandline or you can double click and a package manager (gdebi) will attempt to install it for you.

Here is a howto on using synaptic.
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

When you come across something you may like to install, always go to synaptic first.  Chances are, it's there.  But in some cases, you will find programs that look like package.tar.gz.  Usually this is the source code for the program and you need to "compile it".  This means it has all the code just as the developers wrote it, you need to convert it to machine language.

Edit:  I should mention that rpm is used by red hat based systems (Redhat Package Manager).  Ubuntu is a debian based system.  Don't worry too much about that, Ubuntu is approximately Debian.  There are ways of making an rpm into a deb, but it is a last resort.

---

### Post by tgalati4 on 2007-06-17
Usually you hear about a cool program by reading these forums.  Then you install it and try it yourself:

sudo apt-get install thecoolprogramyoujustreadaboutandcantwaittotryout

---

