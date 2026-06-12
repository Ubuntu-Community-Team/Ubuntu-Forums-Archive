---
title: "I'm stuck in a couple quirks"
date: 2005-05-18
forum: Installation &amp; Upgrades
---

### Post by nu2ubuntu on 2005-05-18
](*,) I noticed a couple of funky quirks on the ubuntu 5.04 I recently recieved.
First for some reason, It won't let me log in as root (I get a prompted  that it hates my password) So I can't use any of the configuration tools.  Also it doesn't seem to want to mount my floppy drive.  I figured I'd take a peek at the mnt directory but none of the drives were there.  the drives appear to be located in the computer menu.  I could log in as root fine in the terminal.  Does all the configuration need to be terminal based?  and as for the drives Do I need to edit fstab?  This is the first debian based system that most of my computers actually liked. (except the old emachine it hates everything but RH8.0!) I like to over extend new operating systems to see what it takes to make it crash, so in that aspect 5.04 is holding up.  I just wish I could use the configuring tools.  I sure could use a good linux publication or   some tips or something.  Any thoughts?

---

### Post by bruizer on 2005-05-18
I also left red hat for this far superior distro!! Stability meets cutting edge!

The issue with not being able to log in as ROOT is by design. You specifically need to state that you want to be able to log in as root.

Go to /etc/gdm/gdm.conf
Go to the [security] section, and set
AllowRoot=true

To use anything in the term, use sudo:
sudo ifconfig - for example

Check out ubuntuguide.org for a good starter.
Enjoy!

---

### Post by bored2k on 2005-05-18
1. [http://www.ubuntulinux.org/wiki/RootSudo](http://www.ubuntulinux.org/wiki/RootSudo) . When you get asked for a passwd, use yours.

---

