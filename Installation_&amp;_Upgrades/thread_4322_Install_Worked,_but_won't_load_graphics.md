---
title: "Install Worked, but won't load graphics"
date: 2004-11-13
forum: Installation &amp; Upgrades
---

### Post by qrc on 2004-11-13
Hi, I installed Ubuntu linux on my computer, but instead of a graphical interface asking me for my password, everything was text-based.  Even if I restart my computer, it just asks me for username and password from the shell.  How do I get into GNOME, and why didn't it work initially?

---

### Post by Jspired on 2004-11-14
What are the specs of your PC?  Have you tried typing "startx" (minus the quotes)?

---

### Post by qrc on 2004-11-14
I'm on an AMD Athlon processor, with 256 MB RAM, 120 GB hard drive space, uhhh not sure what else to say about computer specs...

But I never tried typing "startx."  Would it load X window system or whatever?

---

### Post by Jspired on 2004-11-14
It should, yes.  Are you getting any errors?  Try "startx" and let us know what happens.

---

### Post by candymanobh3 on 2004-11-14
What video card are you using?

---

### Post by qrc on 2004-11-14
Thanks for the help guys, but the problem seemed to have occured elsewhere.  After attempting to re-install the OS, I did one thing different than what I did before, which was that I chose not to download the extra packages (since I wanted to test "startx" quickly; my Internet is going really slow today).  Downloading extra packages seemed to have messed it up, but now the GUI is working.

So now, my only left qustion is, as an Ubuntu newbie, what command I could run later on when my Internet is going faster that will download those update packages that I chose not to install during installation?

---

### Post by Jspired on 2004-11-14
Open a console and type "apt-get upgrade" or "apt-get dist-upgrade."  That will take care of the updates.

As someone asked before, what video card are you running?

---

