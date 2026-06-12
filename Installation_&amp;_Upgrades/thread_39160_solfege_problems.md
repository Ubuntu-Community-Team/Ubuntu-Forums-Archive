---
title: "solfege problems"
date: 2005-06-03
forum: Installation &amp; Upgrades
---

### Post by thnogueira on 2005-06-03
Hi all,

I'm trying to install solfege in my Ubuntu box but I'm having some problems. The apt-get solfege command was ok, but when I try to run it, I got the folloing error:
> 
/usr/share/solfege/src/mainwin.py:108: GtkDeprecationWarning: gtk.TRUE is deprecated, use True instead
  self.set_resizable(gtk.TRUE)
/usr/share/solfege/src/mainwin.py:133: GtkDeprecationWarning: gtk.mainiteration is deprecated, use gtk.main_iteration instead
  gtk.mainiteration(0)
/usr/share/solfege/src/mainwin.py:126: GtkDeprecationWarning: gtk.mainiteration is deprecated, use gtk.main_iteration instead
  gtk.mainiteration(0)
/usr/share/solfege/src/tracebackwindow.py:28: GtkDeprecationWarning: gtk.FALSE is deprecated, use False instead
  self.vbox.pack_start(label, gtk.FALSE)
/usr/share/solfege/src/tracebackwindow.py:30: GtkDeprecationWarning: gtk.TRUE is deprecated, use True instead
  label.set_line_wrap(gtk.TRUE)
/usr/share/solfege/src/tracebackwindow.py:31: GtkDeprecationWarning: gtk.FALSE is deprecated, use False instead
  self.vbox.pack_start(label, gtk.FALSE)
Traceback (most recent call last):
  File "/usr/bin/solfege", line 46, in ?
    import src.mainwin
  File "/usr/share/solfege/src/mainwin.py", line 167, in ?
    from htmlwidget import HtmlWidget
  File "/usr/share/solfege/src/htmlwidget.py", line 611, in ?
    import gtkhtml2
ImportError: No module named gtkhtml2
nogueira@lfnl02:~$ solfege
/usr/share/solfege/src/mainwin.py:108: GtkDeprecationWarning: gtk.TRUE is deprecated, use True instead
  self.set_resizable(gtk.TRUE)
/usr/share/solfege/src/mainwin.py:133: GtkDeprecationWarning: gtk.mainiteration is deprecated, use gtk.main_iteration instead
  gtk.mainiteration(0)
/usr/share/solfege/src/mainwin.py:126: GtkDeprecationWarning: gtk.mainiteration is deprecated, use gtk.main_iteration instead
  gtk.mainiteration(0)
/usr/share/solfege/src/tracebackwindow.py:28: GtkDeprecationWarning: gtk.FALSE is deprecated, use False instead
  self.vbox.pack_start(label, gtk.FALSE)
/usr/share/solfege/src/tracebackwindow.py:30: GtkDeprecationWarning: gtk.TRUE is deprecated, use True instead
  label.set_line_wrap(gtk.TRUE)
/usr/share/solfege/src/tracebackwindow.py:31: GtkDeprecationWarning: gtk.FALSE is deprecated, use False instead
  self.vbox.pack_start(label, gtk.FALSE)
Traceback (most recent call last):
  File "/usr/bin/solfege", line 46, in ?
    import src.mainwin
  File "/usr/share/solfege/src/mainwin.py", line 167, in ?
    from htmlwidget import HtmlWidget
  File "/usr/share/solfege/src/htmlwidget.py", line 611, in ?
    import gtkhtml2
ImportError: No module named gtkhtml2


I tried installing libgtkhtml20, libgtkhtml2-0, libgtkhtml2-dev, libgtkhtml2-ruby and gtkhtml packages without results.

Could someone help me?

---

### Post by Karlos on 2005-07-01
I have the same..
I suspect it is a case of installing a -dev library
I'll let ya know if I suss it out

---

### Post by Karlos on 2005-07-01
I seem to be entering dependancy hell now

libgtkhtml2-dev needs libgail-dev but not gonna be installed (etc)
libgail-dev needs libgtk2.0-dev (>= 2.2.0-2) but it is not going to be installed
 Depends: libgnomecanvas2-dev (>= 2.4.0) but it is not going to be installed

so on and bla

I reckon that somewhere round here lies our problem

I'm gonna look for a .deb package or maybe install from source

I have tried enabling the demudi repos but had no success

any bright ideas on this one would be gratefully received

---

### Post by Karlos on 2005-07-01
OK here's what you do

go to 

[http://www.solfege.org/Main/Download](http://www.solfege.org/Main/Download)

download the autopackage installer (I went for the development version)

make it executable (properties>permissions tick the box)

click on it

it connects to net and installs all relevant libs. then a nice windowsy GUI appears and program gets installed.

nice

---

### Post by Karlos on 2005-07-04
by the way 

if anyone looks at this thread and does the same thing be aware that solfege wont fire up until you type in the command

/home/karlos/.local/bin/solfege

obviously replace karlos with your own home directory

I made a shortcut on the gnome taskbar

now that I have it working I can say that it is brilliant well worth checking out if your a muso like me

---

### Post by arphe_el on 2006-02-14
[QUOTE=Karlos]by the way 

if anyone looks at this thread and does the same thing be aware that solfege wont fire up until you type in the command

/home/karlos/.local/bin/solfege

obviously replace karlos with your own home directory

I made a shortcut on the gnome taskbar

now that I have it working I can say that it is brilliant well worth checking out if your a muso like me[/QUOTE]

any step by step procedure on how to make it executable and how to fire it up? thank you I appreciate your help. GODspeed!

---

