---
title: "Give me a newbie guide on how to install a firewall/iptables"
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by Lord Xeb on 2008-01-18
I am very new to linux *since 2-3 days ago* and I am trying to set up a firewall..... please help (I am going to need as detailed of a description as possible) I understand ssome of the basics

---

### Post by oldos2er on 2008-01-18
Ubuntu comes with a firewall already installed, called IPtables. If you'd like a GUI program to configure IPtables, search Synaptic Package Manager for Firestarter.

---

### Post by Pumalite on 2008-01-18
Or Guarddog

---

### Post by Lord Xeb on 2008-01-18
I got the file now on my desktop, but when I enter in sudo apt-get install firestarter it says that it isn't there,obsolete, or isn't availible.....

---

### Post by oldos2er on 2008-01-18
> **Lord Xeb said:**
> I got the file now on my desktop, but when I enter in sudo apt-get install firestarter it says that it isn't there,obsolete, or isn't availible.....

 apt-get and Synaptic search for files in the repositories; they don't "know" about files you've downloaded to your desktop. Can you post the output of the command (typed in a terminal) "cat /etc/apt/sources.list"?

---

### Post by zvacet on 2008-01-19
If you downloaded deb file on your desktop just double click on it.Better way is to install it with synaptic.In synaptic type in search box firestarter and when you find it mark for install.Of course you need all repos to be open,so system>administration>software sources>chek all under Ubuntu software and updates tab.Reload.

---

### Post by Lord Xeb on 2008-01-20
I added the screen shots of the terminal to this post

---

### Post by Pumalite on 2008-01-20
Post your sources list as you were told and change your colours. I can't see!(copy and paste from the Terminal)

---

### Post by oldos2er on 2008-01-20
> **Lord Xeb said:**
> I added the screen shots of the terminal to this post

 Type "gksudo gedit /etc/apt/sources.list" in a terminal, then remove every comment mark (#) from the lines beginning with deb and deb-src. You can safely skip the backports section. Save the file, then run

sudo aptitude update

 You shoud be able to install firestarter now.

---

### Post by Lord Xeb on 2008-01-20
I already got it guys, thanks (I found a deb file finally)

---

