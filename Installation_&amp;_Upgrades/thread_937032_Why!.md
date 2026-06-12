---
title: "Why!?"
date: 2008-10-03
forum: Installation &amp; Upgrades
---

### Post by TheKnowledge on 2008-10-03
Why is it so complicated to install software on linux? Why can't they just make so that I can dobbelclick on a file and it will install? I cant install emerald or awn, or java or anything! I love linux, but this is so frustrating! btw, is it possible to get emerald, awn and java as a .deb file?

---

### Post by lukjad on 2008-10-03
Well, I'm not sure of specifics, but I have rarely had to compile my own programs unless I wanted the bleeding edge stuff. Usually it is in Synaptic or comes in a .deb file.

---

### Post by kshane on 2008-10-03
> **TheKnowledge said:**
> Why is it so complicated to install software on linux? Why can't they just make so that I can dobbelclick on a file and it will install? I cant install emerald or awn, or java or anything! I love linux, but this is so frustrating! btw, is it possible to get emerald, awn and java as a .deb file?

These are all easy to install (just a click).  What are you trying to do???

Kevin

---

### Post by growingneeds on 2008-10-03
Linux is different from Windows. But ubuntu has made it less strenuous for the average Linux user. I'm not too certain what you require. But if you require Java for browsing purposes (internet banking etc), I'd recommend Ubuntu Restricted Extras. Just go to Add/ Remove Programs and search for Ubuntu Restricted Extras. Make sure that All Available Applications is enabled. Install that meta-package. It will take a while. But it will bring in lots of functionality into Ubuntu.

Is there any other software you'd like to bring up?

---

### Post by perlluver on 2008-10-03
Emerald, can be found in Synaptic, and AWN, can be found in Add/Remove Programs.  There is also [http://www.getdeb.net](http://www.getdeb.net) , for all your .deb files.

---

### Post by Rocket2DMn on 2008-10-03
Most any software you will ever need is available in the repositories, which you use a package manager to access.  Synaptic is the primary GUI based package manager, and apt-get is the standard terminal based manager.  Have a look at [uhelp]community/InstallingSoftware[/uhelp], [uhelp]community/SynapticHowto[/uhelp], and [uhelp]community/AptGet/Howto[/uhelp].

You can also install software from source, but this is not the recommended approach unless you absolutely have to.  If a program isn't available in the repositories, you should check the project website to see if you can get a .deb file, otherwise check getdeb.net as was suggested earlier.

---

### Post by howefield on 2008-10-03
> **TheKnowledge said:**
> Why is it so complicated to install software on linux? Why can't they just make so that I can dobbelclick on a file and it will install? I cant install emerald or awn, or java or anything! I love linux, but this is so frustrating! btw, is it possible to get emerald, awn and java as a .deb file?

got to say, absolutely love your handle :guitar:

---

### Post by SunnyRabbiera on 2008-10-03
> **TheKnowledge said:**
> Why is it so complicated to install software on linux? Why can't they just make so that I can dobbelclick on a file and it will install? I cant install emerald or awn, or java or anything! I love linux, but this is so frustrating! btw, is it possible to get emerald, awn and java as a .deb file?

It is easy to install these things under linux if you know how.
getdeb as installer files as does [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by TheKnowledge on 2008-10-04
thanks guys, this is the error message I get when I ./configure

configure: error: C compiler cannot create executables

and when I type "make" and "make install" it just says "no such file or command or whatever"

---

### Post by TheKnowledge on 2008-10-04
> **howefield said:**
> got to say, absolutely love your handle :guitar:

:popcorn:

---

### Post by Rocket2DMn on 2008-10-04
Have you installed the build-essential metapackage?  This contains all the necessary compilers to build programs from source.
```
sudo apt-get install build-essential
```

---

### Post by oldos2er on 2008-10-04
> **TheKnowledge said:**
> thanks guys, this is the error message I get when I ./configure

configure: error: C compiler cannot create executables

and when I type "make" and "make install" it just says "no such file or command or whatever"

 You need to install the package build-essential.

 Why not install programs the easy way and use Synaptic Package Manager, or Add/Remove Software?

---

### Post by TheKnowledge on 2008-10-06
thanks guys, pieces are falling into place here now.

---

