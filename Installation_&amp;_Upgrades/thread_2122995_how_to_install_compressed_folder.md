---
title: "how to install compressed folder"
date: 2013-03-06
forum: Installation &amp; Upgrades
---

### Post by EDDIH on 2013-03-06
Hi guys. i am trying to learn how to install a software that is compressed(tar.gz). how do i go about it (especially through the terminal). i am still new to linux, so baby steps for me please.

---

### Post by bfmetcalf on 2013-03-06
It's actually pretty easy.  This page should help a bit and I will give some instructions below.  [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

If you have the build-essential package installed you can just do this on most Linux Distro's.  I'm going to assume you downloaded the package freecad.tar.gz to your Downloads folder...

This will get you into your downloads folder
```
cd ~/Downloads
```

now we unpack the tar file
```
 tar xvf freecad.tar.gz
```

now we go into the folder it made and run make
```
cd freecad/
make
```

now we install the package
```
make install
```

This will install it but you will need to install the same way each time you want to update it.

---

### Post by Cheesemill on 2013-03-06
That all depends on the software.

A tar.gz is equivalent to a .zip file, it can contain absolutely anything.

In the case of software delivered as a .tar.gz file it could contain source code that needs to be compiled, it could contain a precompiled binary, or it could contain .deb files.
The method for installation is completely dependant on what is inside the .tar.gz file, you will usually find that it contains a README file with instructions.

Is there any particular application that you are trying to install, or was this a general question?

---

