---
title: "does this hurt anything??"
date: 2005-02-03
forum: Installation &amp; Upgrades
---

### Post by uberlinux on 2005-02-03
Hi all, 
  New to synaptic/ubuntu/debian.....  I was wanting to clean things up after the initial install to get rid of thing I wont use, so I started tracking them down in synaptic, and for each thing I want to remove, It says it will also remove things like Gnome-base etc. Would removing something like eveloution really make synaptic remove gnome... or would it just alter it?  Would removing base items like mozilla etc. cause system stability?
can I create a user to try this on without hurting my real user and root accounts?
 =D>  Thanks in advance, Gurus =D>

---

### Post by az on 2005-02-03
Usually these are meta-packages.  They are empty packages that depend on others.  It is safe to remove them.  If it is problematic (in the event that you remove something other than a meta-package)  just reinstall it.

No, you cannot do this for only one user.  The applications are either installed or they are not.


For example, ubuntu-desktop is a meta-package.  If you remove one element on which it depends, you will also have to remove it.  That does not mean that the other fifty packages on which it depends will dissapear, nor will they neccessarily stop working.

Just keep an eye on what youare removing and you should have some idea of what you are doing.

---

### Post by Rancoras on 2005-02-03
[QUOTE=uberlinux]Would removing base items like mozilla etc. cause system stability?[/QUOTE]

Actually, removing Windows causes system stability.  ;)

(but I knew what you meant, hehe)

---

### Post by uberlinux on 2005-02-03
[QUOTE=azz]Usually these are meta-packages.  They are empty packages that depend on others.  It is safe to remove them.  [/QUOTE]

Is there any way of finding which are and which arent??

---

