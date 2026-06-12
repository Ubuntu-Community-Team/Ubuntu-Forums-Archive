---
title: "GTK objects not displaying"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by rolandz on 2007-11-06
After an upgrade from feisty to gutsy (done by the book) with a crash in the middle of it I have a problem with the dialog boxes that use GTK like Appearance. It now says [a GTKIconView] or [a GTKComboBox] instead of the actual graphical element. Everything else works just fine (such as compiz and AVN) but some applications that use GTK like gnome-rdp and the (presumably) the printing administration application won't start. Since i'm not very familiar with linux (i'm a windows administrator 8-[) i've tried reinstalling a few packages (gtk, libglib) but all to no avail. Does anyone have a clue what the problem might be and, more importantly, a solution?

---

### Post by sibir on 2008-03-10
I've just recently upgraded to Gutsy from Feisty and experienced the same problem.  I have compiz running along with Emerald, AWN, and i've just recently installed Gnome-Do. I'm running all that on a Dell Inspiron 1505, which came with Feisty installed from Dell, back in June of '07.

The widgets that don't render are - 

Gtk icon
Gtk ComboBox
Gtk ColorButton
Gtk ToolButton

etc

Also, I've just been getting into gtk programming with glade, but i can't correlate this problem with my use of glade exactly.

---

### Post by sibir on 2008-03-10
Specifically, I've noticed this happening in System->Peferences->Appearance.

[IMG]http://www.plantimals.org/blog/Appearance_Preferences.gif[/IMG]

---

### Post by sibir on 2008-03-11
I found the solution, and it only took 24 hours!

The issue is with ldconfig.   Check out this [launchpad bug report]("https://bugs.launchpad.net/ubuntu/+source/compizconfig-settings-manager/+bug/129816").  Most of the way down in the comments, itze suggests the working solution. In my case, I found a collection of libglade libraries:

libglade-2.0.a 
libglade-2.0.la 
libglade-2.0.so
libglade-2.0.so.0
libglade-2.0.so.0.0.1


Once I removed these, the Gtk objects/widget problem was no more.

I did not put these library files into the /usr/local/lib.  This occured after installing several dev packages for glade and gtk, though I can't say which one did this.  If anyone has any ideas on how I might track down exactly what caused this, I'd love to give it a shot.

My first attempt at tracking this down is this, I've checked the creation times for the libglade files and crossreferenced them with my synaptic log and narrowed the offending packages to this list:

Removed the following packages:
glade-gnome

Installed the following packages:
devhelp (0.13-2ubuntu1)
devhelp-common (0.13-2ubuntu1)
freeglut3-dev (2.4.0-5)
glade (2.12.1-6ubuntu2)
glade-doc (2.12.1-6ubuntu2)
glade-gnome-3 (3.2.0-0ubuntu1)
libdevhelp-1-0 (0.13-2ubuntu1)
libglade-cil (1:1.0.10-5build3)
libglade0 (1:0.17-8 )
libgladeui-1-dev (3.2.0-0ubuntu1)
libgladexml-perl (0.7009-12)
libglib-cil (1:1.0.10-5build3)
libgtk-cil (1:1.0.10-5build3)
libgtk-perl (0.7009-12)
libxml1 (1:1.8.17-14build1)

---

