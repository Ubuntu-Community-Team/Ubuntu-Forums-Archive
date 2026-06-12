---
title: "Installing a program for just one user"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by feedmecereal on 2008-10-31
Is it possible to install a program for just one user without that user having to enter an administrative password?

I don't actually need this but I am curious.

---

### Post by martrn on 2008-10-31
It depends what you mean by install.  Most packages compiled for ubuntu are debs and most of these will dictate that the file system is owned by root when it creates a file structure or places a binary file in a folder.  

You can put or even install if you like, a binary file anywhere eg /usr/games  for a selection of games.

To install or put a binary file to your file system that only one user can execute you could put it or install it to your home folder.  Or put it in the general file system and change ownership(chown) and change the file permissions for the executable file.

Most of those in the ubuntus apt-repository do not do this.

---

