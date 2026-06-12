---
title: "[SOLVED] Suddenly aptitude doesn't trust Universe"
date: 2008-03-22
forum: Installation &amp; Upgrades
---

### Post by Nameless_one on 2008-03-22
Today I tried to install some packages (anjuta, git-svn), and aptitude told me that they come from untristed sources. I checked, and they are from Universe. 

I use aptitude from the command line, and today I opened the UI version to try some things, but I didn't do anything other than searching and then quitting. I can't imagine what could have caused this.

---

### Post by Shazaam on 2008-03-22
Try this.......
```
sudo aptitude update
```
or...
```
sudo apt-get update
```
See if this cures your problem.

---

### Post by Nameless_one on 2008-03-23
That actually did it, thanks. Why did it happen, though, can you explain?

---

