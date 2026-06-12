---
title: "Setting up eclipse autocomplete for pygtk"
date: 2008-10-15
forum: Installation &amp; Upgrades
---

### Post by Radioactiveroach on 2008-10-15
Google searching around I noticed that that there where very few if any articles in the forums that really touched on this subject. For all the people that use eclipse this can be quite frustrating. So after figuring out I decided to post this article on what I did to get autocomplete working for pygtk.

First I should let you know a little information about my system I am running Gutsy Gibbon (using Linux Kernel 2.6.22-14-rt) on a Dell Inspiron 1501.
  
I installed eclipse via repositories using Synaptics package manager as well as eclipse-pydev, python-gtk2-dev, python-gnome2-dev, glade-3 and python-glade.

I am not sure where I read it but according to an Ubuntu forum I read Eclipse -pydev searches in /usr/lib/python for the modules it needs by default. However the modules for pygtk are located in /var/libs/python-support.

To correct this go to Window->Preferences->Pydev->Interpreter-Python. Under this dialog you should see a section called "System PYTHONPATH" click on the right-hand button labeled "New Folder" and add the Folder /var/libs/python-support I added every folder under this one as well (I'm not sure if that was necessary).

According to [PyGTK FAQ]("http://faq.pygtk.org/index.py?req=show&file=faq23.043.htp") You also need to go to "Forced builtin libs" in the same dialog and click the "New" button on the right-hand side to add gtk, gobject, pango, and atk (Note: click the "New" button for each one). 

Click the apply button on the bottom and once Eclipse finishes searching everything you should now have autocomplete working for gtk (and more).

I hope this helps:)
and happy programming.

Please let me know how it works for you and what you did below also let me know if there are any errors.

---

### Post by nadavvin on 2008-12-03
I did what you mention but Eclipse isn't autocomplete for pygtk:
[[IMG]http://img70.imageshack.us/img70/516/eclipseconfigzr8.th.png[/IMG]](http://img70.imageshack.us/my.php?image=eclipseconfigzr8.png)

---

### Post by Radioactiveroach on 2008-12-03
> **nadavvin said:**
> I did what you mention but Eclipse isn't autocomplete for pygtk:
[[IMG]http://img70.imageshack.us/img70/516/eclipseconfigzr8.th.png[/IMG]](http://img70.imageshack.us/my.php?image=eclipseconfigzr8.png)
Your image doesn't show your "/var/libs/python-support" directory as being included into your System PYTHONPATH section add this directory to the section (Note: paragraph 4). Then try it again (if you haven't done so already). Also, don't forget about pango and atk (Note: paragraph 6).

---

### Post by chongzi35 on 2008-12-03
High pressure power **[cast steel valves](http://www.valvesupplier.net/cast-steel-gate-valves.htm)** are a key piece of equipment used in the power generation industry, high alloy [cast steel valve]("http://www.valvesupplier.net/cast-steel-gate-valves.htm") is required I the main steam, auxiliary steam and water supply systems.

---

### Post by nadavvin on 2008-12-04
Thanks it's work now.

However, It isn't complete from instances, for example:
img = gtk.Image()

It's only suggest built in methods of python which start and end in '__'

---

### Post by Radioactiveroach on 2008-12-04
> **nadavvin said:**
> Thanks it's work now.

However, It isn't complete from instances, for example:
img = gtk.Image()

It's only suggest built in methods of python which start and end in '__'
Do you have pango and atk in the "Forced builtin libs" section? If not make sure those are included as well.
after typing...
import pygtk
pygtk.require('2.0')
import gtk

img = gtk.image()
img.get()

You should start typing "get" to come up with suggestion that begin with "get".

---

### Post by nadavvin on 2008-12-04
> **Radioactiveroach said:**
> Do you have pango and atk in the "Forced builtin libs" section? If not make sure those are included as well.

yes
> **Radioactiveroach said:**
> 
after typing...
import pygtk
pygtk.require('2.0')
import gtk

img = gtk.image()
img.get()

You should start typing "get" to come up with suggestion that begin with "get".

I get suggestion in your code, but I don't get suggestion in my code.
for example in the code I post here:
[http://www.gtkforums.com/viewtopic.php?t=2262#6120](http://www.gtkforums.com/viewtopic.php?t=2262#6120)

---

### Post by Jack Kelly on 2012-07-12
Hi,

Just to bring this thread up-to-date... has anyone got full autocompletion in PyDev working for GTK3 and pygobject?  I've put the following paths into my system PYTHONPATH:

/usr/lib/python2.7/dist-packages/gi
/usr/lib/python2.7/dist-packages/gobject
/usr/lib/python2.7/dist-packages/glib

Some autocomplete works (e.g. Gtk.Window will autocomplete) but others do not (e.g. Gtk.Box).

Any thoughts?

---

### Post by Jack Kelly on 2012-07-12
OK, fixed it:

You don't need to add the paths I listed above.  Neither do you need to add "gtk", "gobject", "pango" and "atk" to "Forced Builtins".  Instead just add "gi" to "Forced Builtins", as per [this stack overflow answer]("http://stackoverflow.com/a/7505814/732596").

---

