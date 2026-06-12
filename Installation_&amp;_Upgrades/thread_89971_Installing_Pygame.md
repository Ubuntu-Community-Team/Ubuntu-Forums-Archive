---
title: "Installing Pygame"
date: 2005-11-13
forum: Installation &amp; Upgrades
---

### Post by Gaucho4SSS on 2005-11-13
Hi, I would like to start doing some development with Pygame but cant get it installed on Hoary. In fact, I cant even find it withing the Package manager. Searches for pygame reveal nothing( as well as searches for python2.4-pygame, etc...) and I have basically looked through the entire updated package manager for the pygame package. Am I missing something here??

---

### Post by tehwa on 2005-11-14
It should be in universe:

[http://packages.ubuntu.com/hoary/python/python-pygame](http://packages.ubuntu.com/hoary/python/python-pygame)

Check that you have enabled the Hoary universe in your apt sources:```

deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe
```

---

