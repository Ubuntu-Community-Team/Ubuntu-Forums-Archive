---
title: "question about installed packages"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by bongoMaster on 2007-11-14
Hello,

does somebody know a way to find out to which repository listed in /etc/apt/sources.list an installed package belongs? I would like to delete some items in my /etc/apt/sources.list, but before I would like to know if I have some packages from those repositories installed. Thanks!

Pascal

---

### Post by kyphi on 2007-11-14
If you enter the Synaptic Package Manager under System, Administration, you will find in the bottom left corner a selection of buttons.  Press 'Sections' and you can get some idea on where your installed files have come from.  Your installed files are all marked.

Rather than deleting entries in your sources list, why not just put ## at the beginning of the lines that you do not want, then save.  That way, if you have made a mistake, or change your mind later, you can restore those lines with ease.

Any entry that includes the name ubuntu you most definitely should keep.

---

### Post by bongoMaster on 2007-11-14
Thanks for the answer. I never used Synaptic, don't like GUIs that much ;) Isn't there an apt or dpkg command to provide this information?

> Rather than deleting entries in your sources list, why not just put ## at the beginning of the lines that you do not want, then save. That way, if you have made a mistake, or change your mind later, you can restore those lines with ease.

for sure :) I'm afraid that if I remove or comment out a source in sources.list, I'd maybe not get security updates any more if I still have packages from those sources installed. I had the backports-repository enabled, and I would like to go back to a system without backports...

ciao,
Pascal

---

### Post by kyphi on 2007-11-14
You could try ```
apt-cache
```and in particular ```
apt-cache showsrc <name>
```Synaptic makes it just so much quicker.

---

### Post by bongoMaster on 2007-11-15
that's roughly the same as

```
dpkg -s <name>
```

It gives lots of interesting informations, like name and email of the maintainers, exact version number, etc..., but that's not exactly what I search. Most of the time you can deduce what repostory it belongs to from this informations, but not always...

for example, the ideal command would give something like that:

```
pp@gutsy:~$ *desired-command* libdvdcss2
http://packages.medibuntu.org/ gutsy free

```

In the "Sections" field of synaptic,I couldn't find a section called "medibuntu". If I search for libdvdcss2, only the version (1.2.9-2medibuntu4) shows me that the package comes from medibuntu. But not all packages have the repository-name in their version number.

I searched quite much,finaly I don't think that such a command exists, but anyway it would be nice...

---

### Post by bongoMaster on 2007-11-15
Sorry, looked again at synaptic, and I found what I'm looking for :). Not with the "sections" button, but with the "origin" or "source" button (traduction from german, don't know whow it is called in english). That's nice. But I still would prefer a command for the command-line...

---

### Post by kyphi on 2007-11-15
Medibuntu is not in Synaptic.

Sorry that I cannot help with finding a command line solution for you.  I have not yet come to that part of the book.

Synaptic will give you the answer in the meantime.

---

### Post by bongoMaster on 2007-11-16
finaly i think I can live without that command line solution, thank you for helping :)

> Medibuntu is not in Synaptic.
I don't agree with this statement. Everything you put into your sources.list ist listed in Synaptic and in any other package manager,,, 

ciao
Pascal

---

### Post by kyphi on 2007-11-16
Ah yes, if you have installed Medibuntu it will be in Synaptic.

I have not installed Medibuntu therefore it is not in my Synaptic entries.

There are two commands that you can use to find the sources:

```
apt-cache policy <programme name>
``` and ```
apt-cache madison <programme name>
```

---

### Post by bongoMaster on 2007-11-18
Thanks!!! Exactly what I wanted :) :) :) U rock :guitar:

---

