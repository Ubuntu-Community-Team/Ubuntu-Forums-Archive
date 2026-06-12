---
title: "gdlib"
date: 2005-09-18
forum: Installation &amp; Upgrades
---

### Post by jabb0 on 2005-09-18
hey folks,

I have a section in a webpage which manipulates an image using the GD library.
I have setup an apache server with php4 and mysql as detailed on the ubuntuguide.org.
The problem is that i am now receiving errors about unknown function and the like due to this image maipulating section of my site.

I am assuming that gdlib does not come as standard with my chosen installation method, it is not detailed in my php.ini file. 

This is not critical, but the thing is i have all this setup on my local machine which i use to develop code - so it would be real nice if i could get this to work.

Has anyone got any ideas as to how i would get the GD library installed and usable?

---

### Post by pete on 2005-10-17
Maybe you already got this done, but if not, this should do it:

[INDENT]sudo apt-get install php4-gd[/INDENT]

---

