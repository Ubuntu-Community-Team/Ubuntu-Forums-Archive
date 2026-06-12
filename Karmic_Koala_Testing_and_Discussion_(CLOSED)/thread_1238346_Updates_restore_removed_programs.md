---
title: "Updates restore removed programs?"
date: 2009-08-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Pat L.I. on 2009-08-12
Hello, Im currently running Karmic on my eeepc900 and I am loving it. The netbook is much snappier and responsive. 

quick question. I have removed certain programs/packages of which I do not need. Such as games, office, bluetooth, etc etc. however when I run my updates everything is restored.

I do not remember this always being the case. Am I missing something? is there a way to have the system automatically update only the packages I have installed?
thank you!

---

### Post by taavikko on 2009-08-12
> **Pat L.I. said:**
> Hello, Im currently running Karmic on my eeepc900 and I am loving it. The netbook is much snappier and responsive. 

quick question. I have removed certain programs/packages of which I do not need. Such as games, office, bluetooth, etc etc. however when I run my updates everything is restored.

I do not remember this always being the case. Am I missing something? is there a way to have the system automatically update only the packages I have installed?
thank you!

ubuntu-desktop is responsible for that action, remove it and your clear to remove any package you desire.
(packages that are dependant of it)

CAUTION: without it you'll miss what would finally be official-release.
You'll just have the updated packages and such.

---

### Post by bear24rw on 2009-08-12
how did you remove them? did you aptitude purge?

---

### Post by Pat L.I. on 2009-08-12
First I used the Add/Remove Programs from the main programs menu to remove what I could.

After that I just went through synaptic and did 'mark for complete removal' of everything else.

---

### Post by phenest on 2009-08-12
I always lock the package version in Synaptic. Uninstall the package, then lock the package version: Menu bar > Package > Lock Version.

---

### Post by Pat L.I. on 2009-08-12
Ah thank you. I will lock the packages.

@Taavikko - thanks for the word of caution. However I plan on doing a fresh install when the final version is released.

---

### Post by Kow on 2009-08-12
I usually keep ubuntu-desktop removed. The problem is if ubuntu adds a package to it that has not been previously installed.... and you want added packages to the meta-list to be installed. So locking packages is probably the best option.

---

### Post by Toe on 2009-08-12
You do not have to remove the ubuntu-desktop package.

Using aptitude with the -R parameter (telling it not to install recommended packages) will allow for an upgrade of the ubuntu-desktop metapackage without re-installing unwanted programs (such as bluetooth in your case).

e.g.:
sudo aptitude safe-upgrade -R
sudo aptitude install ubuntu-desktop -R

---

