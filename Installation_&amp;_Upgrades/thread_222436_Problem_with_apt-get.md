---
title: "Problem with apt-get"
date: 2006-07-25
forum: Installation &amp; Upgrades
---

### Post by jfefhjsdf on 2006-07-25
I just installed ubuntu and I'm trying to install gtkpod
using apt-get.  Unfortunately, it seems that I need to
edit some source file somewhere as I get the following error:

$ sudo apt-get install gtkpod
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gtkpod

It seems that as a new member of the forum, I am not allowed
to perform any searches on the forum.  Could somebody clue me
in on where the file is that I need to edit to be able to
install gtkpod?

Thanks.

---

### Post by Titus A Duxass on 2006-07-25
The source can be found in /etc/apt.  Do sudo pico /etc/apt/sources.list and then edit that file.

You will have to find out which repository has the required files and then add that repository to the list.

Or, remove the # from in front of any lines that look like a web address.
Then do sudo apt-get update,
Then try sudo apt-get install (your package here).

---

### Post by linear on 2006-07-25
gtkpod is in the Universe repository. For future reference, you can search for packages at [http://packages.ubuntu.com](http://packages.ubuntu.com).

---

