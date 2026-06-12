---
title: "Find and install dependency"
date: 2007-07-09
forum: Installation &amp; Upgrades
---

### Post by Custom_Cowboy on 2007-07-09
A very fresh to Fiesty operator here. Trying to install kmymoney from their site and get a dependency message referring to kdelibs4. How do I search for this? Can it be done from the terminal and if so what commands. Also where do I find a list of the commands.

---

### Post by ajgreeny on 2007-07-09
In a terminal type:-
**sudo apt-get install kmymoney2**
and this will sort out all the dependencies for you, or use synaptic which will do the same.
You should seldom need to go to the program's own site to download and then install, just use Ubuntu's repositories.

---

### Post by poohbear1616 on 2007-07-09
> How do I search for this? Can it be done from the terminal and if so what commands

For future reference to search for something in terminal use this:

```
sudo apt-cache search <package name>
```

---

