---
title: "Is there a way to regress all packages / reset the installation?"
date: 2006-08-28
forum: Installation &amp; Upgrades
---

### Post by dpaint4 on 2006-08-28
I've enjoyed Dapper Drake a whole lot. Too much, in fact. I've installed crazy things with crazy dependencies, and I've lost track of it all.

I'd like to remove all the packages that I installed and their dependencies without having to do a clean install from disk, though I'll do that if that's the only way.

Right now nothing is 'broken' or functioning poorly, but I'm very aware of the build-up. 

The benefit to doing things the way I wish I could would be that I could keep all my files, but lose all the stupid applications I tried.

---

### Post by spin2cool on 2006-08-28
I don't know of a 'revert' command, but you can start by uninstalling a package you know about, say emacs:

```
sudo apt-get remove emacs21
```

Then, run deborphan to find out what dependencies that left laying around

```
sudo deborphan
```

If they all look all right to remove, remove them!

```
sudo deborphan | sudo xargs apt-get remove -y
```

Rinse, lather and repeat.

In all honestly, it might be easier to do a reinstall, though.  Because, you know, your important files are all backed up anyway (right?!?!)

In the future, you also might consider putting your home directory on a seperate partition, so you can reinstall without losing anything.

---

### Post by dpaint4 on 2006-08-28
I like your last idea. My files are backed up, indeed, but there are many many discs and always the paranoia that I've missed something.

I'm going to do a fresh install and this time when the installer asks, I'm going to make myself an additional partition just for my home directory.

Thanks for the tip.

---

