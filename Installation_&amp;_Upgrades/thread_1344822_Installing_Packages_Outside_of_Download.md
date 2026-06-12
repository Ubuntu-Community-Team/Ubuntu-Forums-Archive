---
title: "Installing Packages Outside of Download"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by rsupansic on 2009-12-03
I installed Jaunty Jackalope 9.04 from a CD. I have been unable to set up an internet connection because certain packages have not been installed.  I downloaded them using another machine and copied them to /var/cache/apt/archives.  Neither Applications >Add/Remove Packages nor Administration > Synaptic Package Manager recognizes these packages.

1. Am I limited to only installing from the existing package manager list?  Note that dpkg is not in the package list.
2. In the terminal window, sudo apt-get install [package] produces a "package not found" error.
3. When copying to the "archives" directory, should I copy the original download file or unzip it first and copy the unzipped files?

I would appreciate any help.

---

### Post by quixote on 2009-12-04
1) I've never heard of directly copying to /var/cache/apt as a way to get the system to see packages.  That's definitely not the usual way of doing it.  The default is to look in the repositories (used by dpkg, apt and synaptic).  The equivalent for local packages on your own machine is "gdebi."  More on that in a minute.  

2) You could burn the missing packages to CD and then, under System --Administration --Software Sources, under the "Third Party Software" tab, click on the "Add CD-ROM" button.

3) If the downloaded packages end in .deb, then you can install them with gdebi (assuming that's available, of course). ```
sudo gdebi *package-name.deb*
```However, given that you say you don't have dpkg, possibly you don't have gdebi either.

However, and this would really be my recommendation, if for some reason the install didn't complete right, why not just reinstall and hope it goes better this time?  Or do you have a reason why you need to try to recover the not-so-good install?  It's almost always easier to just start over than to try to fix what didn't work.

---

### Post by rsupansic on 2009-12-07
I don't know which documentation provided the suggestion of using /var/cache/apt/archives.

I found the simple answer:

1.  In nautilus, find the package file.
2.  Right-click on the file.
3.  Select "Open with Archive Manager".
4.  Enter the superuser password, if prompted.

I found this by accident.  The Package Manager documentation does not seem to include it!!!????

---

### Post by quixote on 2009-12-07
Archive Manager extracts (=unpacks) the files.  Sometimes, that's enough to install them.  For instance, Firefox works that way.  Usually, though, that's just the first step, and then you have to install using the unpacked files.  That uses either dpkg, apt (and its GUI, Synaptic), aptitude, or gdebi.

---

