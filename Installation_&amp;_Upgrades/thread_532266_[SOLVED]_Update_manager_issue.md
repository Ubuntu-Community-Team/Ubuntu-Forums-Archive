---
title: "[SOLVED] Update manager issue"
date: 2007-08-22
forum: Installation &amp; Upgrades
---

### Post by deep-z on 2007-08-22
Hi, everyone!

Today I upgraded to latest compiz. Everything went fine, but there is one package remaining forever (yet) in update manager (screenshot attached to this post).

Notice that the package update is the same version as installed already.
After "installation" process it remains as new (the same is happening when performing **sudo aptitude install compiz-core** or doing **reinstall** for this package).

Any ideas, solutions?

---

### Post by bapoumba on 2007-08-22
Please try:
```
sudo aptitude update
sudo aptitude dist-upgrade
```

---

### Post by deep-z on 2007-08-22
Already tried. Doesn't help.

Only solution to get rid of update manager icon in tray is run:
**sudo dselect**, unselect **compiz-core** package, configure and quit **dselect**.

But I think this is not an option, since this package will not update in future.
There is a similiar thread in this forum about some other package locking into update manager also.

Can't figure out, is this an package or update manager bug yet.

---

### Post by HeavyAl on 2007-08-22
I've got the same problem after using the Amaranth guide to installing compiz-fusion. The blasted compiz-core keeps being listed as needing updated but never actually does its thing since the version that says it wants to update is the same version installed.

Anyone know how to stop this behavior?

---

### Post by HeavyAl on 2007-08-22
FYI, anyone following this thread - check out this OTHER thread that shows how to fix the problem:

[http://ubuntuforums.org/showthread.php?p=3222864](http://ubuntuforums.org/showthread.php?p=3222864)

---

### Post by deep-z on 2007-08-22
This solution can BREAK your system! It wants to uninstall **ubuntu-desktop** package!
Also it managed to break my current compiz installation :mad: :E

---

### Post by Netsurfer on 2007-08-22
I am the same problem after install. :(
IMHO the problem is in the package tha has an invalid level. We have to wait for next path to solve it.

Meanwhile, any idea how to manually patch it?  :lolflag:

Bye

---

### Post by deep-z on 2007-08-22
Currently having broken compiz package, wich I can't uninstall or reinstall without remowing ubuntu-desktop! (pretty angry now...)

Any real solutions?

---

### Post by bapoumba on 2007-08-22
Are they bug reports on this?
Might consider filing one.

---

### Post by deep-z on 2007-08-22
There were no progress in fixing broken package with **apitude**, so I tried Synaptic Package Manager.

*** Remove Amaranth repository lines from your** /etc/apt/sources.list** and leave these two:
[INDENT]deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
[/INDENT]

Did** sudo aptitude update**.

Did select custom filters and then Broken. Afterwards marked all broken packages for "Mark all upgrades" and it seems that it fixed the broken compiz package.

Now checking if everything's solved.

---

### Post by deep-z on 2007-08-22
Compiz package installed the latest from the repos below, but plugins and extras packages remained old from Amaranth repository.

So now compiz launches without any plugins:
> 
[01:09:26 deep-z ~]$ /usr/bin/compiz.real (core) - Error: Can't load plugin 'ccp' because it is built for ABI version 20070708 and actual version is 20070815
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'ccp'


I wonder, what to do now....

---

### Post by deep-z on 2007-08-22
So ... saga continues ;) ...

With Synaptic searched for compiz and removed all old 0.5.2* compiz plugins and extras packages (with deps).
Then issued:

> sudo apt-get install compiz compizconfig-settings-manager compiz-fusion-plugins-extra

It reinstalled 0.5.2~git20070817+3v1ubuntu0 packages and afterwards compiz worked again:

> compiz --replace &

Hope it helps, folks.

---

