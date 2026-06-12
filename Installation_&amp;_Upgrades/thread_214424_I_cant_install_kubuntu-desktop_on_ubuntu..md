---
title: "I cant install kubuntu-desktop on ubuntu."
date: 2006-07-12
forum: Installation &amp; Upgrades
---

### Post by tylerjroach on 2006-07-12
I have install kubuntu-desktop to run kubuntu and ubuntu by choice before, but I decided I liked gnome better and i deleted kubuntu-desktop. I have decided I want to try kde again but I cant. When I try to install kubuntu-desktop it says

kubuntu-desktop:
 Depends: kdegraphics-kfile-plugins but it is not going to be installed.

So, then I try to install that file but trying to install it an error message pops up and says

kdegraphics-kfile-plugins:
 Depends: libpoppler1-qt but it is not going to be installed

So, once again I try to install this file but an error message says

libpoppler1-qt:
  Depends: libpoppler1 (=0.5.1-0ubuntu7) but 0.5.3-0ubuntu1 is to be installed

I instead installed kde-core, but I would rather have all of kubuntu.
Any help would be greatly appreciated

---

### Post by gratefultux on 2006-07-12
I dunno why this is happening to you, but it could be because of an upgrade between removing kubuntu-desktop and now.  Kubuntu-desktop is just a meta-package, so "apt-get remove kubuntu-desktop" doesn't remove any of the programs that were installed along with it.  How did you remove kubuntu-desktop.  If you only did the above apt-get remove...then try using this [guide]("http://doc.gwos.org/index.php/Uninstall_kubuntu-desktop") to remove the other packages, and then try to apt-get kubuntu-desktop again.  (I never tried this guide, so be careful, you don't want to remove programs you still want).

---

### Post by T700 on 2006-07-12
What method are you using to try and install KDE?

Paul

---

### Post by aysiu on 2006-07-12
Sounds as if you have conflicting repositories in your sources.list. Get a fresh list:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Then try again: ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```

---

### Post by idonthack on 2006-07-19
I have the same problem, even using only official repositories. My sources.list is the same as the page aysiu linked to.
```
antswin@boromir:~$ sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: kdegraphics-kfile-plugins but it is not going to be installed
E: Broken packages

```

```
libpoppler1-qt:
Depends: libpoppler1 (=0.5.1-0ubuntu7) but 0.5.3-0ubuntu1 is to be installed
```Tyler is probably right about this causing it.

Does anybody know how to fix this?

EDIT: I would also like to add I have never had kubuntu installed before.

EDIT2: I have submitted a bug report (it is a problem with libpoppler1-qt) but I would be grateful for a temporary fix.

---

### Post by dnashark on 2006-08-17
The problem is the libpoppler1 package which is downloaded when you install Compiz. To get past this, you would have to force use of the Dapper version of libpoppler1. Of course, this would then break Compiz.

---

### Post by foxjwill on 2006-08-28
> **dnashark said:**
> To get past this, you would have to force use of the Dapper version of libpoppler1.

I'm having the same problem. How would I force use of the Dapper version of libpoppler1?

EDIT: With help from #ubuntu, I figured out that what was needed was to:
[LIST=1]
[*]Open Synaptic
[*]search for *libpoppler1*
[*]highlight it and click *package -> force version* and then select the dapper version.
[/LIST]

---

### Post by jeremyh on 2006-09-24
I had the same problem, but to correctly install KDE with Compiz, make sure you have the repositories in your apt config.

```

deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main

```

When you have those it'll provide libpoppler-qt1 v0.5.3.

---

