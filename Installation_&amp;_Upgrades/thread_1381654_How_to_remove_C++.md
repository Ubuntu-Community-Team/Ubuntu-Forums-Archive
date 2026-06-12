---
title: "How to remove C++"
date: 2010-01-15
forum: Installation &amp; Upgrades
---

### Post by penguin5 on 2010-01-15
My recent attempts at making games work with Wine  properly I managed to somehow install a lot of programs and files I do not think I need. I am also a ubuntu novice and I would like to know how to properly remove Microsoft Visual C++. Currently it shows that i have the 2005 C++ installed along with two different versions of 2008 versions as well. Unless I am not understanding something you only need one of those am I correct? When I go thorough the Add/Remove it gives me an error: PROGRAM ERROR the program msiexec.exe has encountered a serious problem and needs to close. 

Any help would be much appreciated. Thanks!

---

### Post by rusivi on 2010-08-10
> **penguin5 said:**
> My recent attempts at making games work with Wine  properly I managed to somehow install a lot of programs and files I do not think I need. I am also a ubuntu novice and I would like to know how to properly remove Microsoft Visual C++. Currently it shows that i have the 2005 C++ installed along with two different versions of 2008 versions as well. Unless I am not understanding something you only need one of those am I correct? When I go thorough the Add/Remove it gives me an error: PROGRAM ERROR the program msiexec.exe has encountered a serious problem and needs to close. 

Any help would be much appreciated. Thanks!

As you have experienced, Wine is a work in progress with certain applications and functionality. 

The clean uninstall functionality your looking for is not fully realized in Wine (and Windows for that matter but that's a different topic for a different post) so you have to "engineer" it. 

What I recommend that you do is virutalize Ubuntu (I use VirtualBox) and install the Wine package in a Ubuntu virtual machine, then save a copy of the state of the VM (snapshotting, fully VM copy, etc.). Whenever you encounter a misbehaving Wine application that interferes with your other Wine applications just trash the VM and fire up your snapshot. Wa'la! You just engineered a clean uninstall without wasting time debugging it, nor trashing your .wine folder and having to reinstall all the other programs!

Unless your a Wine/Windows developer, your going to chase down the rabbit hole trying to find a "solution" to your problem which ultimately, most likely entails developing/improving Wine code.

if you are feel free!!!! But, as you noted your a novice so... hope that helps!

---

