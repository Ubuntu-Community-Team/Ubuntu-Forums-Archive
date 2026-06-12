---
title: "Does some body can tell how to install gimpsplugins in ubuntu 9.04"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by roquin on 2009-11-20
Hi, everybody, Does some body can tell how to install gimpsplugins in ubuntu 9.04 thanks in advance

---

### Post by SteveDee on 2009-11-20
> **roquin said:**
> Hi, everybody, Does some body can tell how to install gimpsplugins in ubuntu 9.04 thanks in advance

You may find the answer here: [http://docs.gimp.org/en/gimp-scripting.html#id3112595](http://docs.gimp.org/en/gimp-scripting.html#id3112595)

---

### Post by adaucourt on 2009-11-20
> **roquin said:**
> Hi, everybody, Does some body can tell how to install gimpsplugins in ubuntu 9.04 thanks in advance

Open up the folder containing the plugin. Now, copy the files to the clipboard (Select the files, right click one and press copy)


 On Windows, go to folder GIMP is installed in (usually somewhere in Program Files). Once in the GIMP's main folder navigate to lib\gimp\*version*\ where as *version* represents the version of The Gimp. Then double click the "plug-ins" folder.


 On GNU/Linux, you might need to look around. Plugins will be usually stored under $HOME/.gimp-*.* (where you should replace *$HOME* with path to your home catalogue and gimp-*.* with the version you use (for example 2.6)), but this will install the plug-in locally. If you want to install it globally, you might have a bit more problem. Some boxes will have plugins stored at /opt/gnome/lib/gimp/2.0/plug-ins/ (change lib to lib64 if you've got a 64bit OS), others /usr/lib/gimp/2.0/plug-ins/ (change lib to lib64 if you've got a 64bit OS, although "*$whereis gimp*" (or "*which gimp*") command might help. Note that you have to be root to access these files. For example, if the output was /some/place/bin/gimp, then you could check the /some/place/lib (or lib64 if you've got a 64bit OS).

---

