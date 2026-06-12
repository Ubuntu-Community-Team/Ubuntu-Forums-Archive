---
title: "Dist-upgrade keeps installing random apps"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by midwesterndirt on 2009-12-30
Every time I run dist-upgrade, programs like Abiword, Liferea, Gnome Office and Transmission keep trying to install themselves. This doesn't happen when running "apt-get upgrade." It seems like base install apps are being automatically installed. Can anyone explain why this is happening as this is not how it used to work. Has the functionality of apt-get commands changed with 9.10?

UPDATE: The Update Manager GUI is doing this too.

---

### Post by fancypiper on 2009-12-30
Try this:

sudo apt-get update && sudo apt-get autoremove

---

### Post by midwesterndirt on 2009-12-30
> **fancypiper said:**
> Try this:

sudo apt-get update && sudo apt-get autoremove

I had actually done an autoremove before I attempted to update today and the result has been the same. I don't understand what happened, but suddenly Ubuntu is deciding which apps I should install? It doesn't make sense.

---

### Post by fancypiper on 2009-12-30
AFAIK, the programs work the same, at least, I haven't experienced any differences.

It sounds as if those programs may be dependant upon other programs.

Try removing each one individually and the app should show you why it is attempting to upgrade them.

---

### Post by midwesterndirt on 2009-12-30
> **fancypiper said:**
> AFAIK, the programs work the same, at least, I haven't experienced any differences.

It sounds as if those programs may be dependant upon other programs.

Try removing each one individually and the app should show you why it is attempting to upgrade them.

I think you mean that other apps are dependent on them, but I don't think that is true. For example, I can't imagine any app that would be dependent on Transmission. All I know is this only started happening since my upgrade to 9.10. I see no evidence of unresolved or broken dependencies, because "apt-get install -f" yields no results. Here is what I'm seeing after they've been removed:

```
$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  abiword abiword-common abiword-help abiword-plugin-grammar
  abiword-plugin-mathview evolution evolution-exchange evolution-plugins
  gnome-office gnumeric gnumeric-common gnumeric-doc libaiksaurus-1.2-0c2a
  libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libgdome2-0
  libgdome2-cpp-smart0c2a libgtkmathview0c2a liblink-grammar4 libloudmouth1-0
  libots0 libpst4 libt1-5 liferea liferea-data link-grammar-dictionaries-en
  planner transmission-gtk
The following packages have been kept back:
  gnome mysql-client mysql-client-5.0
0 upgraded, 28 newly installed, 0 to remove and 3 not upgraded.
Need to get 24.0MB/24.7MB of archives.
After this operation, 94.7MB of additional disk space will be used.
Do you want to continue [Y/n]?

```

I've also attached a screen shot of Update Manager.

---

### Post by midwesterndirt on 2009-12-30
I've discovered the problem. I had an old gnome package (probably leftover from 9.04 or earlier) that "could not install." You can actually see it at the bottom of the previously posted screen shot. I removed the package and the other applications stopped trying to invade. Solved!

---

### Post by fancypiper on 2009-12-30
I'm glad you solved it!

[Mark Your Thread as [SOLVED] After Getting Your Answer](http://ubuntuforums.org/showpost.php?p=4527051&postcount=6)

---

