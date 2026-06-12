---
title: "help!!!"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by nobby2k7 on 2007-10-19
plz can anyone help me i dnt now how to install things it wont let me it says something about not being able to open a automatic installation

---

### Post by jrasmussen0 on 2007-10-19
What exactly does it say?  Does it say anything about 'apt-get -f'?

---

### Post by nobby2k7 on 2007-10-19
it says this all the time "" Cannot open /home/nobby/dfbhdSetup.exe: No application suitable for automatic installation is available for handling this kind of file""

---

### Post by forestpixie on 2007-10-19
that's a windows file - you either need to use [wine]("http://www.winehq.org/") or windows :)

what exactly is the file supposed to install, there might be an equivalent

you can get wine from the repos, open a terminal and run this

```
sudo apt-get install wine
```

not sure how to use it thtough

---

### Post by yookoala on 2007-10-19
You can't just installa Windows application to Linux.

Either you need to:
[list]
[*]use a linux version of it
[*]use a linux application that have the same function
[*]install the app on top of [WINE](https://wiki.ubuntu.com/Wine)
[/list]

---

### Post by Cannaregio on 2007-10-19
> **nobby2k7 said:**
> plz can anyone help me i dnt now how to install things it wont let me it says something about not being able to open a automatic installation

[COLOR="Blue"]i dnt now how to install things[/COLOR]

which things?

[COLOR="#0000ff"]it wont let me [/COLOR]

how?

[COLOR="#0000ff"]it says something about not being able to open a automatic installation[/COLOR]

what does it exactly say? Which 'automatic installation'?

------------

I'm not nitpicking. Either you are precise and tell us what's EXACTLY wrong, or there will be noway anybody can really figure or guess what your problems are.

Learn describing what's happening to you, it will also prolly turn out to be useful when you'll visit a doctor, a lawyer or a girlfriend.

---

### Post by nobby2k7 on 2007-10-19
im trying to instal two things football manager 2008 and bitcomet

---

### Post by forestpixie on 2007-10-19
you could have a look at wine hq see if anyone's got the game going 

as far as bitcomet goes there's a whole bunch of torrent apps that work just fine ktorrent and deluge to name 2 - but you might get more suggestions - look in add/remove as a start - search for torrent

---

### Post by nobby2k7 on 2007-10-19
it wont let me install wine its says "Cannot install 'wine'

This application conflicts with other installed software. To install 'wine' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict."

any ideas

---

### Post by yookoala on 2007-10-19
> **nobby2k7 said:**
> it wont let me install wine its says "Cannot install 'wine'

This application conflicts with other installed software. To install 'wine' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict."

any ideas


Launch synaptic to install wine.
Let synaptic handle everything for you.

---

### Post by nobby2k7 on 2007-10-19
nice one mate cheers for that
 wiill i be able to install .exe files now

---

