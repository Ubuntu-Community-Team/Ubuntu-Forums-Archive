---
title: "wxWidget uninstall problem"
date: 2005-05-02
forum: Installation &amp; Upgrades
---

### Post by nemesa on 2005-05-02
Hi!

I've compiled wxWidgets (wx-cvs-20041029.tar.bz2) and now I can't remove it. I copied the directory of the source to /usr/src and I've made:

sudo ./configure
sudo make
sudo make install

And NOW, when I give the command:
sudo make uninstall
--------------------------------------------------------------------
make: Nothing to be done for `uninstall'.
--------------------------------------------------------------------


What can I do now? I don't really want to search through the install script...

---

### Post by nemesa on 2005-05-04
please help me!!

---

### Post by cutOff on 2005-05-04
> sudo make uninstall 
Did you do it from same directory you made 'make install'??

---

### Post by nemesa on 2005-05-04
Yes...But now i've solved it..

I reconfigure the program, with --prefix=/tmp/ --exec-prefix=/tmp/

And then i can see where are the installed files...

---

