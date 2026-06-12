---
title: "Moving to a new system"
date: 2005-08-01
forum: Installation &amp; Upgrades
---

### Post by jnoreiko on 2005-08-01
I'm about to build myself a new system, and I'm going to install Hoary from scratch.

What's the best way to move across all my documents and preferences? Is there any sort of software that does this (like on OS X) or is it just a case of copying the entire home folder?

What about installed applications? Is there a simple way to get the new system to install all the packages I had on the old one?

---

### Post by adwait on 2005-08-01
I guess you could copy the home folders for the preferences. As for the applications.....I guess you'll just have to apt-get them again.........

---

### Post by tom-ubuntu on 2005-08-01
Just use your existing /home folder for all documents and also app settings, if you like. The apps itself need to be installed again, as far as I know.

I migrated myself successfully from Gentoo to Ubuntu, without any problem; just deleted all the app settings folder I didn't need anymore, or didn't like to keep, the rest stayed. Worked without any problem. 

btw. make sure, your /home is on a separate partition, makes your life a lot easier.

---

### Post by adwait on 2005-08-01
Hmm.......now that I am thinking of trying another Distro, dual boot.......I am beginning to see the merits of having that foresite!!

---

### Post by jnoreiko on 2005-08-01
[QUOTE=joeuser]The apps itself need to be installed again, as far as I know.[/QUOTE]

Is it possible to get a plain text list of all currently installed packages?
Given that, it wouldn't be too hard to make a script.

---

### Post by adwait on 2005-08-01
I think this should work:
```
dpkg -l
```

---

