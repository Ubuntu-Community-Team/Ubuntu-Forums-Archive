---
title: "Minimal installer, Full install"
date: 2012-03-22
forum: Installation &amp; Upgrades
---

### Post by tehalynn on 2012-03-22
Is there a way to do a "full" install, but download software after installing rather than as part of the install file? (see description below)

My apologies if this has been answered before.

**Regular method:**

[LIST=1]
[*]Download and burn the install cd, preloaded with the default software selection.
[*]Install from the cd.
[*]Remove undesired software.
[*]Download updates to software.
[/LIST]

[LIST]
[*]Undesired software must be downloaded, installed, then removed.
[*]Updated software is downloaded/installed twice.
[*]The install file is large.
[/LIST]
**Proposed method:**

[LIST=1]
[*]Create an install disk that contains as little software as necessary.
[*]Install from the disk.
[*]Select software to download/install.
[*]Your Ubuntu is now the same as at step 4 of the regular method.
[/LIST]

[LIST]
[*]This installs only what you need.
[*]Software is downloaded only once.
[/LIST]
I know you can use a [minimal cd]("https://help.ubuntu.com/community/Installation/MinimalCD") for steps 1 through 3, but as far as I know, it doesn't do step 4. Is there a good way to do the proposed method?

---

### Post by egeezer on 2012-03-23
You could choose one of the Ubuntu alternate distros like Lubuntu or Xubuntu which are somewhat lighter on the default software side, or some of the derivatives like Bodhi which is much lighter.  If you want to start from an almost empty distro, try Peppermint (One, Two, or Ice).  These are designed to work from cloud apps, but I generally use Synaptic to install on-site (on my hard drive) things like LibreOffice that I use continually.

---

### Post by jerrrys on 2012-03-23
You could use either the mini.iso or the Alternate Install CD to do a terminal only install.  This is a text only install and no GUI will be offered.  Then simply in terminal enter:

sudo apt-get install --no-install-recommends ubuntu-desktop

The standard ubuntu-desktop download is 600+ MB.  This will reduce the Desktop download to 160MB by not installing any recommended packages.

[http://packages.ubuntu.com/oneiric/ubuntu-desktop](http://packages.ubuntu.com/oneiric/ubuntu-desktop)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=mini.iso&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=mini.iso&sa=Search&cof=FORID:9)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=terminal+only+install&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=terminal+only+install&sa=Search&cof=FORID:9)

---

### Post by tehalynn on 2012-03-23
That sounds like what I want. Thanks!

So if I left out "--no-install-recommends", would the result of that be exactly the same as the result of a regular install?

---

### Post by jerrrys on 2012-03-23
> **tehalynn said:**
> That sounds like what I want. Thanks!

So if I left out "--no-install-recommends", would the result of that be exactly the same as the result of a regular install?

yes :)

---

### Post by tehalynn on 2012-03-23
Perfect. Thanks again!

---

