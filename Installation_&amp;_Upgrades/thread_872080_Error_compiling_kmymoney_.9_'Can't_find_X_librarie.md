---
title: "Error compiling kmymoney .9 'Can't find X libraries'"
date: 2008-07-27
forum: Installation &amp; Upgrades
---

### Post by helwitch on 2008-07-27
So, I need some of the features of kmymoney .9, and the kmymoney in the repos is .8.8. So, I'm trying to compile kmymoney from the website download, and when I run ./configure, it dies with the following error.
"checking for X... configure: error: Can't find X libraries. Please check your installation and add the correct paths!"
What do I need to do to make this work? Install some library? append some modifier[LIST]
[/LIST] to the configure command?

---

### Post by oldos2er on 2008-07-27
Usually there is a README or INSTALL  file that tells you the dependencies you need. Or, search Synaptic Package Manager for Xlib-dev (or something similar).

---

### Post by helwitch on 2008-07-28
I installed xlibs-static-dev, didn't help. the readme says the following, which enlightens me not at all about this X error.
> 2)   Run configure to tell the project about your local environment

           ./configure --with-qt-dir=[your location of qt3] \
                       --prefix=[your location of kde3]
And INSTALL says > For packages that use the X Window System, `configure' can usually
find the X include and library files automatically, but if it doesn't,
you can use the `configure' options `--x-includes=DIR' and
`--x-libraries=DIR' to specify their locations.
But I have no idea what directory to list, since I have no idea what files the configure wants!

---

### Post by YEkimV on 2008-08-03
I too ran into the same problem today, and here's what I found (I hope it helps).  Found at: [http://kmymoney2.sourceforge.net/submenu-gen.html](http://kmymoney2.sourceforge.net/submenu-gen.html)



14. Will KMymoney work on my X/Ubuntu desktop?

It will work, but you will have to install the basic KDE libraries first, as Xubuntu comes with Gnome libraries by default. If you want to install from CVS, you should install these packages:

    * build-essential
    * kdelibs4-dev (this one will install a ton of other KDE-related packages)
    * kcontrol (this one will allow you to change KDE-related settings)



P.S.  This worked for me, I'm now using kmymoney on Ubuntu!!!

- YEkimV

---

