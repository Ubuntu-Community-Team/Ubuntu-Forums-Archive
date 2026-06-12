---
title: "APT-GET remove - dependencies"
date: 2005-07-30
forum: Installation &amp; Upgrades
---

### Post by jemt on 2005-07-30
Hi Experts.

Does 'apt-get remove package' remove all dependencies that are no longer needed by the system or other packages?

---

### Post by heimo on 2005-07-30
Good question! apt-get remove (package) will remove package and packages that depend on the package, but it will not remove the packages that were installed because package depended on them...

*lol*

Ok, example. I install ubuntu-desktop and I get a bunch of packages. I remove ubuntu-desktop and nothing else is removed (only the ubuntu-desktop package, not a single package required by this package). I install back that package and remove firefox (which is dependency of ubuntu-desktop), firefox, couple other packages and ubuntu-desktop package will be removed.

---

### Post by jemt on 2005-07-30
Oh, ok. Thanks. Is there somehow i can do a "dep-clean"? I don't like garbage in my system :)

---

### Post by heimo on 2005-07-30
*seriously thinking*

I don't know if that's possible. I know what you mean - but I don't know if that's so simple question for a computer.

If I install aptitude, I will get following packages: aptitude libsigc++-1.2-5 and if I now remove aptitude, I will still have libsigc++-1.2-5 - and no other package needs that library. But I could have installed that library earlier, to be used with program I wrote myself, or compiled from source - and now if removing aptitude would also remove libsigc, my self-compiled application would fail.

However, if we have a "clean" system and no other software besides Ubuntu debs using package management is installed, this cleaning up packages which were installed as a dependency, but are no longer used, could be handy. :)

If you (or anyone here!) knows how to do this, I'm interested too*.


*) As I know something about the Linux community, this can be done, or it's not so useful as we think. :D

---

### Post by kvidell on 2005-07-30
apt-get purge ?
That may do it. There's also the chance that you can use Aptitude and it will do it.
Aptitude will do all the dependancy cleaning if you ask nicely. Just run it from the command line and select a package to remove, it should anull all the deps as well.

This may only work if you installed the package with aptitude initially, I'm not sure.

---

### Post by Xian on 2005-07-30
[QUOTE=jemt]Is there somehow i can do a "dep-clean"? I don't like garbage in my system [/QUOTE]
You just need to install the deborphan package.
```
$ sudo apt-get install deborphan
$ man deborphan
```

---

### Post by heimo on 2005-07-30
Ok... debfoster seems to do something like that.

 ```
Description: Install only wanted Debian packages
 debfoster is a wrapper program for apt and dpkg.  When first run, it
 will ask you which of the installed packages you want to keep
 installed.
 .
 After that, it maintains a list of packages that you want to have
 installed on your system.  It uses this list to detect packages that
 have been installed only because other packages depended on them.  If
 one of these dependencies changes, debfoster will take notice, and
 ask if you want to remove the old package.
 .
 This helps you to maintain a clean Debian install, without old
 (mainly library) packages lying around that aren't used any more.

```

---

### Post by Xian on 2005-07-30
[QUOTE=heimo]Ok... debfoster seems to do something like that.[/QUOTE]
Deborphan requires no setup phase.
IMO it is easier to use.

---

### Post by heimo on 2005-07-30
[QUOTE=Xian]You just need to install the deborphan package.
```
$ sudo apt-get install deborphan
$ man deborphan
```[/QUOTE]

Hey, that's nice - thanks Xian! :) orphaner seems to be frontend to deborhan - very nice.

EDIT: I posted my "debfoster" before I saw your post Xian, deborphan seems a lot easier way to do this maintenance.

---

### Post by jemt on 2005-07-30
Hey, thanks all your guys. That sounds great. I'd like to keep my system clean and tuned. I think you provided my with all the necessary tools - thanks again :)

---

### Post by Xian on 2005-07-30
Here's a few "no dirty hands" deborphan commands:

$ sudo apt-get remove --purge `deborphan`
*Removes and purges the orphan packages*

$ sudo apt-get remove `deborphan`
*Removes the orphan packages*

$ sudo apt-get install wajig
$ sudo wajig orphans
*installs wajig and removes orphan packages*

$ su
$ dpkg --purge `deborphan`
*similar to apt-get --purge*

$ su
$ deborphan | xargs apt-get --purge remove -y
*similar to apt-get --purge*

---

