---
title: "Endless connectivity problems with Medibuntu. Can't upgrade to Gutsy."
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by toggle on 2007-10-20
I can see that a lot of people are having problems upgrading their Feisty installs to Gutsy because of connectivity problems to Medibuntu. I realize its not in the best of taste to complain to people who offer their time and resources for free but can the community of Ubuntu users get some kind of idea of when these problems will be resolved or some kind of workaround that will allow us to upgrade?

This is one area that Ubuntu really falls flat on its face. Its one thing to have high ideals regarding freedom and openness but the fact of the matter is that the available market share Ubuntu is reaching now are primarily Windows users who could not care less and just want their systems to work. These users to not distinguish between the OS (Linux), the distribution (Ubuntu), the UI (Gnome), and the proprietary drivers - all they see is a system that is broken - or as my 15 year old says... Linux sucks.  

Note: the above message was also posted at the Medibuntu site.

---

### Post by bapoumba on 2007-10-20
I use this:
```
# Medibuntu.
deb http://packages.medibuntu.org/ gutsy free non-free
```
In my sources.list. To get the key:
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

But please, comment the medibuntu repos to upgrade (upgrade with basic ubuntu-supported repos), you'll put them back in after.

---

### Post by toggle on 2007-10-20
Thanks very much! That seems to have got my install going.

Its not that I had not considered commenting out those lines in the sources list - its just that I had no idea what the impact of having a system that was part feisty and part gutsy. I figured the safest upgrade was to allow the upgrade manager to make all of the required changes to the existing file.

I imagine that once the upgrade completes I will uncomment the repos and alter any references to feisty with gutsy and then perform another "check" operation.

---

