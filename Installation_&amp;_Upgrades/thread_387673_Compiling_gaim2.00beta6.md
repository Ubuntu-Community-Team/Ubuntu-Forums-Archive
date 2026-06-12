---
title: "Compiling gaim2.00beta6"
date: 2007-03-18
forum: Installation &amp; Upgrades
---

### Post by .Michael on 2007-03-18
I'm trying to compile the latest version of gaim so I can install it.

I get this error on .configure:

> You must have the GLib 2.0 development headers installed to build Gaim.


I cant seem to find them. Are there any other packages I need besides this?

---

### Post by bruenig on 2007-03-18
There are packages out there for this in third party repositories. Here is one such repository: [http://repository.debuntu.org/](http://repository.debuntu.org/)

Here is a command to enable this repository and install beta 6.

```
echo "deb  http://repository.debuntu.org/ edgy multiverse" | sudo tee -a /etc/apt/sources.list && wget http://repository.debuntu.org/GPG-Key-chantra.txt && sudo apt-key add GPG-Key-chantra.txt && rm GPG-Key-chantra.txt && sudo apt-get update && sudo apt-get install gaim
```

If for whatever reason you wish to compile gaim, a good place to start is to do
```
sudo apt-get build-dep gaim
```

The particular problem you are having with that message is no libglib2.0-dev
```
sudo apt-get install libglib2.0-dev
```

---

