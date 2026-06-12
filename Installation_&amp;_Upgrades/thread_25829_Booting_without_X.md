---
title: "Booting without X?"
date: 2005-04-11
forum: Installation &amp; Upgrades
---

### Post by kkathman on 2005-04-11
I'd like to set up an ubuntu box to use just as a file server. This means I really dont need alot of the gtk stuff on the system, and I'd like the system to boot to a command line. There I can configure samba and be able share files across a mixed network.

What exactly do I have to do to get to this environment?  Im assuming I need to remove startx from something, but Im having trouble finding out how.

Thanks for your help!

---

### Post by dabeej on 2005-04-11
You could try booting into changing the init runlevel.

SAVE WHATEVER YOU WERE DOING!!!
Try:

sudo init 1

If this is what you want..

Change from this in /etc/inittab:

# The default runlevel.
id:2:initdefault:


to


# The default runlevel.
id:1:initdefault:


(Notice it's a change from init 1 to 2).

That's it and that's all!

---

### Post by capi on 2005-04-11
[QUOTE=kkathman]I'd like to set up an ubuntu box to use just as a file server. This means I really dont need alot of the gtk stuff on the system, and I'd like the system to boot to a command line. There I can configure samba and be able share files across a mixed network.

What exactly do I have to do to get to this environment?  Im assuming I need to remove startx from something, but Im having trouble finding out how.

Thanks for your help![/QUOTE]
 quite simple, 

$  sudo su
# echo "null" > /etc/X11/default-display-manager
# exit

Then whenever you wan tot go into the GUI just type 'startx' and it will start up. That or when you install Ubuntu type 'server' and it won't install Gnome or any of those packages, very minimal, but at that point you may as well just install Debian instead, a minimal Debian is also smaller.

---

### Post by dusu on 2005-04-11
Hi,

go and see post #4 of [http://www.ubuntuforums.org/showthread.php?t=20140](http://www.ubuntuforums.org/showthread.php?t=20140)
and the link [http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)

There you will see that you can install ubuntu, without all the X-stuff...

But then, of course, you get a minimal system, and lots of things have to be installed by hand.

---

### Post by kkathman on 2005-04-11
Thanks peeps....all of these work like champs I appreciate it!

Kork

---

### Post by Doc.Caliban on 2005-10-29
[QUOTE=dabeej]You could try booting into changing the init runlevel.

SAVE WHATEVER YOU WERE DOING!!!
Try:

sudo init 1

If this is what you want..

Change from this in /etc/inittab:

# The default runlevel.
id:2:initdefault:


to


# The default runlevel.
id:1:initdefault:


(Notice it's a change from init 1 to 2).

That's it and that's all![/QUOTE]


I did this on my own as per the nVidia instructions, and now I can't get into the system.  The loading screen seems to hang about half way.   

Being 24 hours into using linux, I could use some help with this.

-Doc

---

### Post by Doc.Caliban on 2005-10-29
It's stopping at:

"Sending all processes the TERM signal..."

---

