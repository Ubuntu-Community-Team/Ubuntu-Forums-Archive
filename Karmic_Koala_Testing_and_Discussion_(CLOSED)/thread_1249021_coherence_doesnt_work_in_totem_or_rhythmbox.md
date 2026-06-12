---
title: "coherence doesnt work in totem or rhythmbox"
date: 2009-08-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by puccaso on 2009-08-24
as the title says

the coherence upnp plugin isnt working in totem nor in rhythmbox

how do i fix it? what could be the problem
how do i find the problem?

these are the outputs for totem in debug mode

totem:
```
Traceback (most recent call last):
  File "/usr/lib/totem/plugins/coherence_upnp/coherence_upnp.py", line 10, in <module>
    from coherence.ui.av_widgets import TreeWidget
ImportError: No module named coherence.ui.av_widgets

** (totem:7276): WARNING **: Could not load plugin coherence_upnp


** (totem:7276): WARNING **: Error, impossible to activate plugin 'Coherence DLNA/UPnP Client'
mahir@puccaso-lp-nix:~$ 

```

---

### Post by lithorus on 2009-08-25
"python-coherence" was just recently added to replace the old "coherence" package, did you try with that? Works fine here....

> **puccaso said:**
> as the title says

the coherence upnp plugin isnt working in totem nor in rhythmbox

how do i fix it? what could be the problem
how do i find the problem?

these are the outputs for totem in debug mode

totem:
```
Traceback (most recent call last):
  File "/usr/lib/totem/plugins/coherence_upnp/coherence_upnp.py", line 10, in <module>
    from coherence.ui.av_widgets import TreeWidget
ImportError: No module named coherence.ui.av_widgets

** (totem:7276): WARNING **: Could not load plugin coherence_upnp


** (totem:7276): WARNING **: Error, impossible to activate plugin 'Coherence DLNA/UPnP Client'
mahir@puccaso-lp-nix:~$ 

```

---

### Post by puccaso on 2009-08-25
well 
there are two packages, coherence and python-coherence, and they conflict each other..
so i installed python-coherence and totem works, ie - i can activate the plugin, but it doesnt pick up upnp streams/shares on the network

rhythmbox however, doesnt work. 


what do i do?

---

