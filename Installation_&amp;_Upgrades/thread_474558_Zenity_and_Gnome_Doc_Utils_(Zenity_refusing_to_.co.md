---
title: "Zenity and Gnome Doc Utils (Zenity refusing to ./configure)"
date: 2007-06-15
forum: Installation &amp; Upgrades
---

### Post by Tr0janV0dka on 2007-06-15
So, I need Zenity to use grubed ( [http://ubuntuforums.org/showthread.php?t=228104](http://ubuntuforums.org/showthread.php?t=228104) ), and I have used sudo apt-get install gnome-doc-utils and it says it's fully up to date, but Zenity say's otherwise...

tr0janv0dka@Tr0janV0dka-Linux:~/zenity/zenity-2.19.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for pkg-config... no
configure: error: gnome-doc-utils >= 0.3.2 not found
tr0janv0dka@Tr0janV0dka-Linux:~/zenity/zenity-2.19.1$

It's really starting to p*** me off. I go download Zenity, which needs gnome-doc-utils, which in turn needs some random "XML::Perl Parser" (that was before I thought of using apt-get! Guess I don't need the XML::Perl Parser now!). I've just adapted to the whole installing via konsole thing, but the amount of things depending on each other is ridiculous! Do you usually need to restart for some packages to be seen?

Edit: Would it be better to try installing Grub 2? I've read on their website that it does most of the stuff that grubed does (I want to change the positions of where OS's are on the list and set it up so that grub boots into Windows XP after 5-10 seconds, maybe add a splash screen).

Edit2: This error: X Error: BadDevice, invalid or uninitialized input device 167 is also starting to drive me up the wall. I've got a Logitech G15, so maybe that's the problem? I ain't gonna stop using a $130 keyboard because Linux doesn't want to co-operate.

Edit3: Oh joy. One problem after the next. Any clues to solving this one? Gtk-WARNING **: cannot open display:

Anybody who can solve this deserves a medal :D

---

### Post by Tomosaur on 2007-06-15
Zenity is available in the repositories you know, a simple
```

sudo aptitude install zenity

```
should suffice.

This **should** download everything you need to use GTK apps on Kubuntu.

As for your error messages and such, your keyboard could be causing the X Error, but I don't know enough about Logitech keyboards to say for certain. All I can say is to check your /etc/X11/xorg.conf for any obvious problems, and then scour the net.

For your GTK error, I'm just going to assume that you are, in fact, working in GUI mode here? That problem only really occurs when X isn't enabled.

---

