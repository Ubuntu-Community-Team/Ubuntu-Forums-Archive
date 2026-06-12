---
title: "Compiling new kernel. qt libraries not found."
date: 2006-07-16
forum: Installation &amp; Upgrades
---

### Post by harisund on 2006-07-16
```

dpkg --list | grep qt
ii  libqt4-core                            4.1.2-1ubuntu1                        Qt 4 core non-GUI functionality runtime libr
ii  libqt4-dev                             4.1.2-1ubuntu1                        Qt 4 development files
ii  libqt4-gui                             4.1.2-1ubuntu1                        Qt 4 core GUI functionality runtime library
ii  libqt4-qt3support                      4.1.2-1ubuntu1                        Qt 3 compatibility library for Qt 4
ii  libqt4-sql                             4.1.2-1ubuntu1                        Qt 4 SQL database module

```

Any more libraries I need for "make xconfig" ????

Ok, so let's ignore make xconfig. I try make gconfig. 

the make file tells me 
> You need gtk+-2.0, glib-2.0 and libglade-2.0.

Very well. Open synaptic. Search for packages with gtk+ in the name. 

libgtk+2.0-directfb0
libgtk+2.0-directfb-dev

Next, search for packages with glib in the name. A whole bunch appear, so I am guessing the ones I need (which I install) are:
libglib2.0-0
libglib2.0-data
libglib2.0-dev

Now search libglade-2.0. I find it and it is already installed. Thank God. Atleast something. 

I understand Ubuntu is a newbie friendly distro, but does it mean it actually discourages people from compiling their own kernels? Think it is time to switch to Gentoo?

---

### Post by harisund on 2006-07-17
Has no one recompiled their kernels using a GUI? Do Ubuntu users use "make config" or what?

---

### Post by timv on 2007-12-26
One of the less wonderful things about Ubuntu, and I suppose of Unix-y operating systems and free software generally, is that basic questions like this often just don't get answered. Users searching the web to solve a problem can easily find dozens of other users who asked the same question months or years before, but there answers are nowhere to be found.

I don't think it's very likely that the original poster still needs to know this, but for the sake of those like myself who get really frustrated by this: I just solved it by trial and error (for Ubuntu 6.10 Edgy Eft and kernel "2.6.17-12-generic") by installing the packages qt3-dev-tools and libqt3-mt-dev.

I first tried installing some qt4 dev packages and they didn't help. Perhaps I installed something there that was also needed. But adding "qt3-dev-tools" and "libqt3-mt-dev" was what finally made it work for me.

---

### Post by PmDematagoda on 2007-12-26
Why don't you try running:-
```
make menuconfig
```
it seems to have fewer dependencies than the others.

---

### Post by timv on 2007-12-26
> Why don't you try running:-
> Code:
> 
>   make menuconfig

I know how to do that and have used it many times in the past, but I have come to prefer the X interface because it's easier to navigate through the options and browse the choices.

In any case, that wasn't what the original poster was asking about, nor does it answer the question that I had. If "make xconfig" is part of Ubuntu then it seems reasonable to ask for help in using it.

And in fact it was a pretty easy question to answer, even with me pretty much stumbling blindly through the packages.

---

