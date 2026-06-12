---
title: "Help files missing/incomplete after Upgrade to 8.04"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by kamiokande on 2008-07-29
I recently upgraded my Dell XPS m1330 from 7.10 to 8.04 through the update manager. After a few rough spots (namely, freezing during locale generation, as in this thread: [http://ubuntuforums.org/showthread.php?t=865679](http://ubuntuforums.org/showthread.php?t=865679)), I was able to finish the 8.04 upgrade.

However, I now notice that if I attempt to open the Help Center, and for instance click on 'Keeping your computer updated', an error message pops up:

```
Unable to load page: The requested URI "ghelp:keeping-safe#updates" is invalid
```

This occurs with other help options as well. Is this an indication of an incomplete upgrade?

The daily essentials of my computer work fine - internet, playing music, rebooting, etc. 

Does anybody have any solutions for this problem? Thanks for any help!

---

### Post by kamiokande on 2008-07-30
Hm, this seems to be some sort of dependency issue with yelp. When I attempt to upgrade my system (which is up to date, as far as I can tell), I get a message

```
Not all updates can be installed
```

The packages listed in the background when this occurs are 

important security updates:
   firefox
   firefox-gnome-support
   
distribution upgrade:
   librarian0
   yelp

When I open Synaptic and attempt to mark 'yelp' for upgrade, I get this message:

```
Could not mark all packages for installation or upgrade. The following packages have unresolvable dependencies:

yelp
Depends xulrunner-1.9 but it is not going to be installed 

```

The version of yelp that is currently installed is 2.20.0-0ubuntu3, whereas the latest available version is given as 2.22.1-0ubuntu2.

Any thoughts? :-)

---

### Post by kamiokande on 2008-07-30
I marked 'xulrunner-1.9' for installation, but in order to do this it wants to remove both yelp and Ubuntu-desktop, which doesn't seem like a good idea...hmm...stuck here!


Sorry for the repeated posts, but I'm learning new information as I try different things!

---

### Post by SkonesMickLoud on 2008-07-30
Ubuntu-desktop is a meta package, and can safely be removed.  Yelp can be removed and reinstalled.

In a terminal enter:

```
sudo aptitude update && sudo aptitude install xulrunner-1.9 -f
```

Then, if needed, or you want to:

```
sudo aptitude install yelp
```

---

### Post by kamiokande on 2008-07-30
Thanks for your response! I ended up using Synaptic to upgrade firefox to 3.0, that took care of everything in one fell swoop. Apparently I can only have either yelp or firefox 3.0, and not both.

---

### Post by SkonesMickLoud on 2008-07-30
> **kamiokande said:**
> Apparently I can only have either yelp or firefox 3.0, and not both.

Odd.  I've got both.  AFAIK the two have nothing to do with one another, and shouldn't mention one another in their dependencies.

Have you tried installing yelp by itself?

```
sudo aptitude install yelp
```

---

### Post by kamiokande on 2008-07-30
> **SkonesMickLoud said:**
> Odd.  I've got both.  AFAIK the two have nothing to do with one another, and shouldn't mention one another in their dependencies.

Have you tried installing yelp by itself?

```
sudo aptitude install yelp
```

With the command-line install, are you shown what will be removed first? I.E., will it remove firefox without asking me first? (Or perhaps that's what you want to find out?!?)

---

### Post by kamiokande on 2008-07-30
The result of 

```
sudo aptitude install yelp
```

is

```
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
Building tag database...
The following packages are BROKEN:
  xulrunner-1.9 
The following NEW packages will be installed:
  yelp 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 346kB of archives. After unpacking 4059kB will be used.
The following packages have unmet dependencies:
  xulrunner-1.9: Breaks: yelp (< 2.22.1-0ubuntu2.8.04.1) but 2.22.1-0ubuntu2 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
firefox-3.0 [3.0.1+build1+nobinonly-0ubuntu0.8.04.3 (hardy-security, now) ->
3.0~b5+nobinonly-0ubuntu3 (hardy)]
firefox-3.0-gnome-support [3.0.1+build1+nobinonly-0ubuntu0.8.04.3
(hardy-security, now) -> 3.0~b5+nobinonly-0ubuntu3 (hardy)]
xulrunner-1.9 [1.9.0.1+build1+nobinonly-0ubuntu0.8.04.3 (hardy-security, now) ->
1.9~b5+nobinonly-0ubuntu3 (hardy)]
xulrunner-1.9-gnome-support [1.9.0.1+build1+nobinonly-0ubuntu0.8.04.3
(hardy-security, now) -> 1.9~b5+nobinonly-0ubuntu3 (hardy)]

Score is -70
```

---

### Post by kamiokande on 2008-07-30
I've used Synaptic to 'Fix Broken Packages', and it completes successfully after minimal time. However, if I try to install yelp again via the command line, it still considers xulrunner-1.9 a broken package and requests those downgrades!

---

