---
title: "eclipse cant edit .java files?"
date: 2010-02-22
forum: Installation &amp; Upgrades
---

### Post by erjoalgo on 2010-02-22
I installed both eclipse and java runtime through the software center. It opens and I can load my windows workspace fine. But the workspace only shows .class files. There also no option to create a .java files.
Even after creating my own workspace I cant create any .java source files or open the editor.

---

### Post by amsterdamharu on 2010-02-22
You need the jdk (java **development** kit).  Funny that synaptic did not install that along with eclipse. You can use eclipse to develop non java applications so I guess the jre (java **runtime** environment) is enough.

The package name is default-jdk

---

### Post by erjoalgo on 2010-02-22
I installed the jdk, but everytime I open a .java file in eclipse (from the pacakge explorer), it just opens a text editor window (gedit), not the  editor for java source files within eclipse.

The most I can do is open the .java files with the eclipse text editor, but that doesnt allow me to run or edit them.

---

### Post by amsterdamharu on 2010-02-22
Is there anything under:

Help > Software Updates > Find  and Install...

In eclipse? I haven't used it in ages and don't have it installed on ubuntu right now but I think from eclipse you can just about install any plugin you need. But usually it comes with the java already installed, don't know how the ubuntu ppl packaged it but by the looks of it it doesn't make sense.

---

### Post by erjoalgo on 2010-02-22
no, there are no updates, its a new install so there should't be.

---

### Post by amsterdamharu on 2010-02-22
Ubuntu is not fit for programmers, there is not a good package availeble for eclipse. It is best to uninstall and re-install it manually:
[https://help.ubuntu.com/community/EclipseIDE](https://help.ubuntu.com/community/EclipseIDE)
[http://johnpaulett.com/2009/06/26/install-eclipse-galileo-3-5-on-ubuntu-jaunty/](http://johnpaulett.com/2009/06/26/install-eclipse-galileo-3-5-on-ubuntu-jaunty/)

---

### Post by konqueror7 on 2010-02-22
it might be that nautilus is currently binded to using a text editor when .java files are opened... try right clicking the java file, the Properties, then Open With,,,and select or explore Eclipse there...

---

### Post by Mighty_Joe on 2010-02-22
> **amsterdamharu said:**
> Ubuntu is not fit for programmers, there is not a good package availeble for eclipse.

This was true for a long time.  I thought Eclipse had recently been updated to the current version (3.5?).  

@erjoalgo: Did you install the eclipse-jdt (Java Development Toolkit) package?

---

### Post by erjoalgo on 2010-02-22
I followed amsterdamharu's first link and I solved my issue.  Thank you everyone!

---

