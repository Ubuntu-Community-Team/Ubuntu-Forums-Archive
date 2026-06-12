---
title: "Trouble installing mobloquer"
date: 2011-12-10
forum: Installation &amp; Upgrades
---

### Post by alextockey on 2011-12-10
So I'm trying to install mobloquer in Ubuntu.
I downloaded the tar.gz file and used [FONT=Courier New]tar zxf mobloquer-0.6.tar.gz[/FONT]
it created the directory [FONT=Courier New]mobloquer-0.6
[FONT=Verdana]Once i cescended into  the directory and typed[/FONT] ./configure [FONT=Verdana]it showed me this:
[FONT=Courier New]bash: ./configure: No such file or directory[/FONT]
Am I doing something wrong?
[/FONT][/FONT]

---

### Post by yeats on 2011-12-11
Here's a page about installing that on Ubuntu:

[https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock)

Any particular reason you're trying to install from source rather than with the PPA?

If you are committed to continuing with the source install, make sure to read any files named README or INSTALL in the source directory - they probably have clues (if not explicit instructions) for installing.

---

### Post by oldtimer7777 on 2011-12-11
That isn't the way you install moblock successfully, and easily in Ubuntu. You need to install it from the moblock PPA. 

Use the instructions about 1/2 way down this new user checklist:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

It will add the repo you need to download moblock, mobloquer, and install for you automatically. 

> **alextockey said:**
> So I'm trying to install mobloquer in Ubuntu.
I downloaded the tar.gz file and used [FONT=Courier New]tar zxf mobloquer-0.6.tar.gz[/FONT]
it created the directory [FONT=Courier New]mobloquer-0.6
[FONT=Verdana]Once i cescended into  the directory and typed[/FONT] ./configure [FONT=Verdana]it showed me this:
[FONT=Courier New]bash: ./configure: No such file or directory[/FONT]
Am I doing something wrong?
[/FONT][/FONT]

---

### Post by jre on 2011-12-13
Besides just using my ppa (see above posts) I recommend to use pgl from the same source instead.

---

