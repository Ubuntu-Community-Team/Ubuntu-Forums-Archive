---
title: "pygtk just wont work..."
date: 2005-05-05
forum: Installation &amp; Upgrades
---

### Post by D4_B34M on 2005-05-05
Is there a .deb package to pygtk that works on ubuntu?

Ive been fighting with pygtk 2.0 now for 4 hours without result, i can build it, make and make install it, also compiled gnome-python and did the 
export PYTHONPATH=/usr/local/lib/python2.4/site-packages

 but now... What next?? i compiled everything but wheres the executable???
in /usr/local/lib/python2.4/site-packages running pygtk.py shows error:

/usr/local/lib/python2.4/site-packages/pygtk.py: line 27: __all__: command not found
/usr/local/lib/python2.4/site-packages/pygtk.py: line 29: _pygtk_dir_pat: command not found
/usr/local/lib/python2.4/site-packages/pygtk.py: line 31: _pygtk_required_version: command not found
/usr/local/lib/python2.4/site-packages/pygtk.py: line 33: syntax error near unexpected token `('
/usr/local/lib/python2.4/site-packages/pygtk.py: line 33: `def _get_available_versions():'


----
Im getting really angry with this, it _should_  be easy to use but the install part says whole different thing...
Can someone make me step by step manual what to install how to compile... OR is there deb pack what works on Ubuntu?  :neutral: 

P.S. i tried first latest versions and then
gnome-python-2.0.3 + pygtk-2.0.0

---

### Post by Xerampelinae on 2005-05-05
Maybe
```

apt-get install python-gtk2-dev

```

Which I discovered by doing

```

apt-cache search pygtk

```

---

### Post by ow50 on 2005-05-05
[QUOTE=D4_B34M]Is there a .deb package to pygtk that works on ubuntu?[/QUOTE]
python-gtk2
python-gtk2-dev
python-gtk2-doc
python-gtk2-tutorial

python-gnome2
python-gnome2-dev
python-gnome2-extras
python-gnome2-extras-dev

[QUOTE=D4_B34M]i compiled everything but wheres the executable???[/QUOTE]
What are you trying to execute? pygtk.py is not meant to be executed, it's used by apps that are written in PyGTK.

---

### Post by D4_B34M on 2005-05-05
[QUOTE=Xerampelinae]Maybe
```

apt-get install python-gtk2-dev

```

Which I discovered by doing

```

apt-cache search pygtk

```[/QUOTE]


Did that.. now what?

---

### Post by Xerampelinae on 2005-05-05
[QUOTE=ow50]python-gtk2
python-gtk2-dev
python-gtk2-doc
python-gtk2-tutorial

python-gnome2
python-gnome2-dev
python-gnome2-extras
python-gnome2-extras-dev


What are you trying to execute? pygtk.py is not meant to be executed, it's used by apps that are written in PyGTK.[/QUOTE]
 This is a good point... what ARE you trying to execute?

Pygtk is an API for python programmers... allows them to use gtk widgets and stuff.

---

### Post by D4_B34M on 2005-05-05
[QUOTE=Xerampelinae]This is a good point... what ARE you trying to execute?

Pygtk is an API for python programmers... allows them to use gtk widgets and stuff.[/QUOTE]


So.. emn.. my point was to use pygtk in my app.. lol heh.. i misunderstood the the use of pygtk
Heh...

---

