---
title: "Can't make or install/uninstall programs..?"
date: 2007-08-14
forum: Installation &amp; Upgrades
---

### Post by cdeleon on 2007-08-14
First, I'll admit that I've been a Linux user for exactly two days.. so please be patient!

I've got two problems.  First, the 'make' issue - when I run "./configure", I get this error:

checking for C compiler default output... configure: error: C compiler cannot create executables

Then when I try to run 'make' while specifying the makefile, it says "No targets" and aborts.  I've read the installation file, and it just instructed to install by the usual configure/make/install combination.  The same error - the compiler and make - has occured with several packages I've tried.  I've tried a few different things to get past this but it's pretty obvious it's got something to do with the compiler.

The second problem is attempting to add/remove programs; whatever I do, after being authed, it stops and instructs me to run "dpkg --configure -a".  Anyhow, I run the command, evidently need to be a superuser to do so,  and sadly I don't know how to elevate privileges.

Haha.. I feel like such a n00b.  This is what happens after years of Windows..

---

### Post by Steveway on 2007-08-14
sudo dpkg --conffigure -a
And what program do you wanna compile?

---

### Post by cdeleon on 2007-08-14
Haha.. I'm such a Linux newbie.  Thanks :)

Netcat.

---

### Post by Steveway on 2007-08-14
Netcat is in the repositories.
You can either install it using Synaptic or use this command:
sudo apt-get install netcat

---

