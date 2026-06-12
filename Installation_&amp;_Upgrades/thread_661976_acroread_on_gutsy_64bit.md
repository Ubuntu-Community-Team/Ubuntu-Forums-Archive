---
title: "acroread on gutsy 64bit"
date: 2008-01-08
forum: Installation &amp; Upgrades
---

### Post by pranab on 2008-01-08
I installed the acroread, acroread-plugins and acroread-escript on gutsy amd64 machine. When starting from command line acroread complains about qtengine.so like:
> Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so: wrong ELF class: ELFCLASS64

I tried finding the 32 bit gtk libs but I cannot see qtengine.so anywhere. Is it needed? If so which package I should install? Visually I do not see any problem, it displays fine and prints fine too. 

Also, I could not get it work with firefox at all. First of all I could find any package that contains nppdf.so. Finally found it Adobe's tar install file. Then I used nspluginwrapper to wrap it, but firefox tries to load it but does not display anything on the screen. The errors are many and coming from the wrapper itself looks like. Is there a better way of doing this? So far all the tutorials and forums posts have confused me a lot. There is frequent mention of mozilla-acroread package which does not exist for gutsy64.

---

### Post by MobiusNZ on 2008-01-08
You really should have a look round the [x86 64-bit Users]("http://ubuntuforums.org/forumdisplay.php?f=134") section. You may find you're better off using 32bit ubuntu till some of the key desktop machine issues (java, flash, pdf) are fixed.

---

### Post by pranab on 2008-01-08
Found a solution to get rid of the qtengine error in the kubuntu forums. I got hold of ubuntu package for i386 of gtk-qt-engine. Then copied the library file libqtengine.so to the appropriated location on gutsy for 32 libs: /usr/lib32/gtk-2.0/2.10.0/engines

The solution came from an old post for a different problem. The steps are also noted here.
[http://kubuntuforums.net/forums/index.php?topic=4509.0](http://kubuntuforums.net/forums/index.php?topic=4509.0)

Now the error goes away, and there is absolutely no change in the way acroread works. The firefox problem is still unsolved.

I think I will end up installing 32bit firefox eventually.

---

### Post by MobiusNZ on 2008-01-08
> **pranab said:**
> I think I will end up installing 32bit firefox eventually.
Not to be a scaremonger, but if you install 32bit firefox and use CUPS for printing (the default) you won't be able to print from firefox, as CUPS will be 64bit libraries and firefox will look for the 32bit versions.

---

