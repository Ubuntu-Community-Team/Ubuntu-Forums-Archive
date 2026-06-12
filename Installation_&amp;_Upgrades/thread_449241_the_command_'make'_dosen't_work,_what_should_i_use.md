---
title: "the command 'make' dosen't work, what should i use instead?"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by yahon on 2007-05-20
I want to install the MPICH onto my computer.But as the book on my hand writes, I should use 
the command 'make'. In the Terminal of Ubuntu, make doesn't work,What should I use instead?

---

### Post by taurus on 2007-05-20
What is the error message when you try to run the command?  Perhaps you need to install the build-essential package first since you need to install make.

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install build-essential
```

---

