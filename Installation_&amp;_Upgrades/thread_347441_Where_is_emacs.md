---
title: "Where is emacs?"
date: 2007-01-27
forum: Installation &amp; Upgrades
---

### Post by une on 2007-01-27
I created an Ubuntu 6.10 CD to try it out as a Live CD before installing.
I tried to write a simple C++ program in my usual way using emacs.
From the command line in a terminal I entered;
**# emacs test.cpp**
and was told that the emacs command was not found. So I tried
**# xemacs test.cpp**
and got the same result.

Does this package (6.10) have emacs or xemacs in it?
I thought emacs was a pretty standard application in most Linux distros.
If it is included, where is it and why did the above commands not work.
If it is not included, can anyone provide a link to a simple installation guide.
I found a thread in an ubuntu forum about installing a version of emacs with antialiasing but realized very quickly that I could not understand it.

---

### Post by encompass on 2007-01-27
Not that standard anymore... if you want to edit files with the live cd use nano simple fast and easy.
If you plan to program I don't think you can with the live cd of ubuntu.  you could create your own.  But that takes some knowledge.
To edit files try gedit.  Might be a better start for you.

---

### Post by une on 2007-01-27
So I guess emacs is not included and I will have to install it. I am used to the emacs environment as I can edit, compile and view compilation errors without leaving the text editor.

---

### Post by confused57 on 2007-01-27
I installed emacs on a partition running Ubuntu-Lite, but trying to run it I got the error message "termcap data file not found".  I had to install termcap, which had a couple of dependencies that in turn had a couple of dependencies...the dependencies were all .deb files so they were easy to install.
I don't have the links now, but I googled for the termcap error message and found a link that had the necessary dependencies to install.

Probably easier just to install it through Synaptic Package Manager.

---

### Post by encompass on 2007-01-28
99 percent of what you will be using is already built into the repositories that are downloaded automatically.
As for the programming... your gong to need gcc and a few other things... but that list can get very long.  yes your right... when your program you need a lot of things.

---

