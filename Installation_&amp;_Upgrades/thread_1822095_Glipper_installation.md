---
title: "Glipper installation"
date: 2011-08-10
forum: Installation &amp; Upgrades
---

### Post by bloosky on 2011-08-10
Everyone,
Being entirely new to Linux and Ubuntu I'm at a loss here. I'm trying to enable Glipper and can't seem to find a way to do it and no search helped so far. I have a new Ubuntu installation (11.04?) and this is stand alone system with new hard drive and no files outside of Ubuntu OS, but keep in mind computer is NOT connected to internet at this point.

When I try installing Glipper through terminal I get "unable to locate package Glipper"

In Synaptics I cannot locate such package. I have downloaded Glipper 2.1 and extracted it, so I now have it on the desktop. Any ideas?

---

### Post by YannBuntu on 2011-08-10
Hello, and welcome among us. :)

Glipper is in the "Universe" repository, which is not enabled by default in Ubuntu.
To enable it, open the Software Centre (or Synaptic) , then in the menus you should find "Sofware sources", where you will be able to enable Universe. (at the same time, I recommand you enable also "Multiverse")

Then reload your package list, and try again to install Glipper.

If you still can't install it, there are many alternatives.
The one I use is Glippy : [http://www.omgubuntu.co.uk/2010/06/glippy-simple-clipboard-manager-with-image-support/](http://www.omgubuntu.co.uk/2010/06/glippy-simple-clipboard-manager-with-image-support/)

But there are also [Pastie]("http://www.omgubuntu.co.uk/2010/10/pastie-handy-clipboard-manager-indicator-applet/"), [Parcellite]("apt://parcellite") ...

---

### Post by scorp123 on 2011-08-10
You could also use "parcellite" ... it performs the same functions like glipper:

```
sudo apt-get install parcellite
``` Log out, log in again ... taddaaaa, it will be there.

---

