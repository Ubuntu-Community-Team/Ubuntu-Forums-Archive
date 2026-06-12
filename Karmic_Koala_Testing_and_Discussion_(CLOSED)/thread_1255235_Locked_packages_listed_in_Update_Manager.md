---
title: "Locked packages listed in Update Manager"
date: 2009-09-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Sfinx- on 2009-09-01
Hello,

I am running Ubuntu Karmic since a few weeks. In order to use a specific application, I had to lock my SVN packages (subversion, libsvn...) to an earlier version (in the Synaptic Package Manager).

However, when I run the Update Manager, it still lists the packages above as to-be-updated. I have no option to deselect them.

I have ran "aptitude hold <package-name>" for all of these but that didn't seem to work. Is there any other way I can update my system or use the Update Manager without overwriting these packages?

---

I have noticed this is listed as a bug already years ago - but I'm unable to find any sort of solution!

---

### Post by Sfinx- on 2009-09-02
I finally found a quickfix for this issue:

[http://ubuntuforums.org/showthread.php?t=43631](http://ubuntuforums.org/showthread.php?t=43631)

In short:

sudo apt-get install wajig
sudo wajig hold <package>

This thread can be set to resolved!

---

