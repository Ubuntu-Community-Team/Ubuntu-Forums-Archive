---
title: "Installing Val(a)IDE"
date: 2010-11-05
forum: Installation &amp; Upgrades
---

### Post by jlindsay on 2010-11-05
Hello,

First, please excuse me as this is my first time using this forum and I am still quite new to Ubuntu. I'm currently using 10.10 after having upgraded, and I'm really enjoying it so far. I have become interested in the Vala programming language. I would very much like to try out Val(a)IDE but for the likes of me I can't seem to find out how to install it. I've searched for it using the Ubuntu Software Centre and can't find it. I have installed Vala without any issues but can't seem to get any IDE operational.

---

### Post by dino99 on 2010-11-05
open synaptic (system admin synaptic) and search for "vala", you'll see "valac" and its other libs

[https://help.ubuntu.com/community/Vala](https://help.ubuntu.com/community/Vala)

---

### Post by jlindsay on 2010-11-05
Hi dino99,

Thanks for your reply. This truly must be the best community based support of any software! Perhaps I'm just being thick, but following your steps, I still don't see an option for Val(a)IDE. I see plenty of other Vala options (e.g. valac, libvala, Mono's vala plugin), most of which I have already installed, but I don't see Val(a)IDE. Am I doing something wrong?

---

### Post by dino99 on 2010-11-05
cant say much as i've never used Vala

what synaptic doc says about valac:
Vala is a new programming language that aims to bring modern programming
language features to GNOME developers without imposing any additional
runtime requirements and without using a different ABI compared to
applications and libraries written in C.

valac, the Vala compiler, is a self-hosting compiler that translates
Vala source code into C source and header files.  It uses the GObject
type system to create classes and interfaces declared in the Vala
source code. This package also contains the vala-gen-introspect and
vapigen binaries that will automatically generate Vala bindings.

This package always depends on the currently supported version
of valac but doesn't have any content by itself.

[http://live.gnome.org/Vala](http://live.gnome.org/Vala)

---

### Post by jlindsay on 2010-11-05
Okay thanks dino99. I've got Vala installed on my computer but am just looking for a good IDE for it under Ubuntu. It could be that I can't run Val(a)IDE under Ubuntu. I guess I'll just have to figure something else out :)

---

