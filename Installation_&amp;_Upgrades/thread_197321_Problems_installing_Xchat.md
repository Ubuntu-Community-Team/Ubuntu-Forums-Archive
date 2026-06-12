---
title: "Problems installing Xchat"
date: 2006-06-15
forum: Installation &amp; Upgrades
---

### Post by Sir_Sid on 2006-06-15
Ok I just installed the Ubuntu 6.06. This is my first time using linux but I just learned how to compile sources and install them. Im trying to install Xchat. I installed the lastest version of glib. Now im having another problem. When trying to do make install I get the error that it could not find perl.lb (Im not sure about the exact file name) Something to do with perl. Do I need to install Perl to get Xchat working? Is there anything else I need to install to get Xchat working?

---

### Post by bruce89 on 2006-06-15
Xchat is available in the repositories, but it has been superseded with xchat-gnome.  Install it by ```
 apt-get install xchat-gnome
```.  You shouldn't manually install new versions of glib, that will break everything.

---

### Post by kostkon on 2006-06-15
Why do you think you have to compile the programs you want to use. In Linux you use packages that take care of installing every application you need. In Ubuntu you have a collection of 18000+ packages giving you the power to install with just one click almost everything you'll need.

Just run Synaptic, search for xchat and install it. It is a matter of seconds to do this.

---

### Post by Sir_Sid on 2006-06-16
I was told that too but I want to practice on something. I want to learn how to do things in the terminal properly too.

---

