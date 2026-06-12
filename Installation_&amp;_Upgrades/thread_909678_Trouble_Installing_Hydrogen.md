---
title: "Trouble Installing Hydrogen"
date: 2008-09-03
forum: Installation &amp; Upgrades
---

### Post by d3rek on 2008-09-03
I'm tying to install the drum sequencer program 'Hydrogen'

I'm getting this error: 

```
--- Checking for QT Libs ----------------------------------------
checking whether QTDIR environment variable is set... no
configure: WARNING: QTDIR must be properly set.
 * Searching for Qt library
   |-> searching QT in /usr/share/qt *** Not found ***
   |-> searching QT in /usr/share/qt3 *** Not found ***
   |-> searching QT in /usr/lib/qt3 *** Not found ***
   |-> searching QT in /usr/lib/qt-3.1 *** Not found ***
configure: WARNING: Qt library not found. Maybe QTDIR isn't properly set.
checking for qmake... no
configure: error: qmake not found in current PATH. Maybe QT development environment isn't available (qt3-devel).

```

I installed libqt4-core but I'm still getting the same error.

---

### Post by Partyboi2 on 2008-09-03
There is a version of Hydrogen in the ubuntu repo's you can install it by opening a terminal and
```
sudo apt-get install hydrogen
```if you also want the drumkit for hydrogen you can install that as well
```
sudo apt-get install hydrogen-drunkits
```

---

### Post by d3rek on 2008-09-03
Well that's much easier, awesome. thanks so much.

I'd still like to know how to resolve the problem for future reference though.  I've yet to successfully build a program from source.

---

### Post by Partyboi2 on 2008-09-03
> **d3rek said:**
> Well that's much easier, awesome. thanks so much.

I'd still like to know how to resolve the problem for future reference though.  I've yet to successfully build a program from source.

Install libqt3-mt-dev package

---

### Post by d3rek on 2008-09-03
Ok one last thing.  How do I install the ladspa plugins?

---

### Post by Partyboi2 on 2008-09-03
You could try ladspa-sdk package but I am not a 100% sure.
If not have a look [[COLOR=Blue]here[/COLOR]]("http://packages.ubuntu.com/search?keywords=ladspa&searchon=all&suite=all&section=all")

---

