---
title: "tar installs not working"
date: 2007-09-02
forum: Installation &amp; Upgrades
---

### Post by fenario on 2007-09-02
whenever trying to install a tarball this error comes up when doing ./configure:

Package libgnome-2.0 was not found in the pkg-config search path. 
Perhaps you should add the directory containing `libgnome-2.0.pc' to the PKG_CONFIG_PATH environment variable 
No package 'libgnome-2.0' found 

Package libgnomecanvas-2.0 was not found in the pkg-config search path. 
Perhaps you should add the directory containing `libgnomecanvas-2.0.pc' to the PKG_CONFIG_PATH environment variable 
No package 'libgnomecanvas-2.0' found 

Package libbonoboui-2.0 was not found in the pkg-config search path. 
Perhaps you should add the directory containing `libbonoboui-2.0.pc' to the PKG_CONFIG_PATH environment variable 
No package 'libbonoboui-2.0' found 

Package gconf-2.0 was not found in the pkg-config search path. 
Perhaps you should add the directory containing `gconf-2.0.pc' to the PKG_CONFIG_PATH environment variable 
No package 'gconf-2.0' found

configure: error: 
Library requirements (libgnome-2.0 >= 2.0.0 libgnomecanvas-2.0 >= 2.0.0 libbonoboui-2.0 >= 2.0.0 gconf-2.0 >= 1.1.11) not met; 
consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

What needs to be done? So many others encounter this problem as well but I haven't found any answers so far.
Can somebody give me a step by step method on how to fix this problem? Wgere are those files stashed and why is it always expecting it in the wrong place. There has to be an easy fix once and forever.

Thanks my good penguines for an answer.
fen

---

### Post by CRCarl on 2007-09-02
What exactly do you type to get these errors?

C

---

### Post by fenario on 2007-09-10
Hi Carl

I ectract the file, move into the folder and type ./configure

then it does it's thing and brings up these lines saying it cannot find such and such libs.

I don't know what that pkg config path means and where do you add something.

---

