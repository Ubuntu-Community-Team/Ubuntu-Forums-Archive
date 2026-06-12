---
title: "ppa for koffice 2.1.1 for kubuntu 9.10?"
date: 2010-02-04
forum: Installation &amp; Upgrades
---

### Post by Haber_Nir on 2010-02-04
hi all.
is there koffice 2.1.1 ppa for kubuntu 9.10?
thx ahead.
H.N.

---

### Post by oldsam on 2010-02-04
I was searching for the same just now and found this forum entry.
There is a ppa, look here:

[https://launchpad.net/~kubuntu-ppa/+archive/backports?field.series_filter=karmic]("https://launchpad.net/%7Ekubuntu-ppa/+archive/backports?field.series_filter=karmic")

First remove the old installation with
sudo apt-get purge koffice-kde4
sudo apt-get autoremove #to remove existing packages

Then install the new one
sudo apt-get update
sudo apt-get install koffice-kde4

EDIT:
Sorry, but the given steps don't work. Says wrong dependencies.
Maybe someone else has a solution

---

