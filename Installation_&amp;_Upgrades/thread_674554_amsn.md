---
title: "amsn"
date: 2008-01-21
forum: Installation &amp; Upgrades
---

### Post by aja on 2008-01-21
Hello


Does any one have any ideal what I am doing wrong ??  I ve loaded amsn 0.97 form add / remove as well as from synapic package manger. Both cases it show as being loaded OK, But when I start amsn. It does not start ???  All I see is a wheel go around for while then nothing.

---

### Post by Partyboi2 on 2008-01-21
Open a terminal (Applications>Accessories>Terminal) and type
```
amsn
``` Post the output from the terminal. Hopefully this will give a clue to what is happening.

---

### Post by aja on 2008-01-21
me@me-desktop:~$ amsn
/usr/bin/amsn: line 3: exec: wish: not found

---

### Post by Partyboi2 on 2008-01-21
Have a look [here]("http://www.amsn-project.net/forums/viewtopic.php?t=1882&postdays=0&postorder=asc&start=0")

---

### Post by frankos44 on 2008-01-23
I assume you have installed amsn using Add/Remove?
If so, remove it using Add/Remove.

There is a much newer version available that works well on Gutsy.
You can get this from:

[http://sourceforge.net/project/downloading.php?groupname=amsn&filename=amsn-0.97-1.tcl84.x86.package&use_mirror=mesh](http://sourceforge.net/project/downloading.php?groupname=amsn&filename=amsn-0.97-1.tcl84.x86.package&use_mirror=mesh)

After downloading goto the folder where the downloaded file exists

$ sudo apt-get install tclx8.4
$ chmod amsn-0.97-1.tcl84.x86.package 
$ ./amsn-0.97-1.tcl84.x86.package 

Most problems seem to be fixed on this version.

---

