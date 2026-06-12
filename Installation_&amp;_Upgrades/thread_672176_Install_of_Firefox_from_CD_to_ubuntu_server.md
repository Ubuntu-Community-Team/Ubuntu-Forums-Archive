---
title: "Install of Firefox from CD to ubuntu server"
date: 2008-01-19
forum: Installation &amp; Upgrades
---

### Post by erosion on 2008-01-19
:) hello,
I installed ubuntu server edition and then installed LAMP
I need to install firefox web browser on to ubuntu server edition from CD .  and i also need to install phpmyadmin also from the cd .

Anyone got a clue ? How do i copy firefox-2.0.0.11.tar.gz and phpmyadmin-2.11.4-english.tar.gz from CD to the server and where do i put it?

P.S.
Unfortunate that the server setup is not complete yet and it is not networked it yet, but give it a week and i should have it the best way it can be

---

### Post by njparton on 2008-01-19
You need a desktop environment such as gnome before you can install and use programs like firefox.

Ideally you should have gone for the desktop edition, but I beleive you can run the following command to install ubuntu desktop (including gnome and a bunch of other stuff that* may* automatically install firefox for you):

```

sudo apt-get install ubuntu-desktop

```

I think you'll also get openoffice, evolution and a bunch of other stuff that you may or may not need.

I'm not sure how you'd just install gnome and then firefox individually or even whether that's possible/advisable.

---

### Post by erosion on 2008-01-19
> **njparton said:**
> You need a desktop environment such as gnome before you can install and use programs like firefox.

Ideally you should have gone for the desktop edition, but I beleive you can run the following command to install ubuntu desktop (including gnome and a bunch of other stuff that* may* automatically install firefox for you):

```

sudo apt-get install ubuntu-desktop

```

I think you'll also get openoffice, evolution and a bunch of other stuff that you may or may not need.

I'm not sure how you'd just install gnome and then firefox individually or even whether that's possible/advisable.

I need the server edition because i want in to be a server. I tried your sudo apt-get........etc , but the reply was Couldn't find package ubuntu-desktop

---

### Post by njparton on 2008-01-19
The desktop edition contains access to all the same packages as the server edition so there's no worries there.

Server editon leaves you with just a command line server so you won't be able to run any gui programs like web browsers etc.

Search these forums for how to install desktop on top of a server installation, there's loads of info out there. You probably need to enable the correct repositories to get ubuntu-desktop but I've never done that from the command line.

Search the forums, you're not the first one who's done this.

---

### Post by erosion on 2008-01-22
well ..........i am sick of reading ....my brain feels burned and i came to the conclusion that the question shows that i am new to ubuntu server. I still wonder if i installed the GUI for ubuntu server weather or not i then could install firefox. But i just setup the network and now use firefox from a computer running windows XP . [http://servername](http://servername) and that works great.:guitar:

---

