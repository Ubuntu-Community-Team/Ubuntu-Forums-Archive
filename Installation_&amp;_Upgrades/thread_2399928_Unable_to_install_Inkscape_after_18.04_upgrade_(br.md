---
title: "Unable to install Inkscape after 18.04 upgrade (broken packages Synaptic won't fix)"
date: 2018-08-31
forum: Installation &amp; Upgrades
---

### Post by stinktier2 on 2018-08-31
So I upgraded xubuntu 16.04 to 18.04 recently as soon as it became available on the automatic upgrade check. 

Somehow it removed Inkscape which I had installed. No big deal I thought.

But when I try to "Mark for Installation" Inkscape via Synaptic, I can see it is a broken package. Pressing the "Apply" button says so, "*Could not apply changes! Fix broken packages first.*"

When I try to do this ("Fix broken packages" in Synaptic) after I marked Inkscape, I get a pop-up error message:
> E: Unable to correct problems, you have held broken packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
So now I am stumped. After browsing tons of postings I tried to **apt-mark showhold** in the terminal, but this showed nothing.

When I try to install Inkscape manually (**sudo apt install inkscape**), this shows up:
> Reading package lists... Done
Building dependency tree       

Reading state information... Done

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

The following information may help to resolve the situation:


The following packages have unmet dependencies:
 inkscape : Depends: libgsl23 but it is not going to be installed

            Depends: libgslcblas0 but it is not going to be installed

E: Unable to correct problems, you have held broken packages.

How do I fix this?

---

### Post by Perfect Storm on 2018-08-31
Hi,
Try with
```
sudo apt --fix-broken install
```

---

### Post by stinktier2 on 2018-08-31
> **Artificial Intelligence said:**
> Hi,
Try with
```
sudo apt --fix-broken install
```
This shows just;
> The following packages were automatically installed and are no longer required:
  fonts-oxygen libastro1-qt4 libboost-regex1.58.0 libcdr-0.1-1 libgc1c2 libgps22 libgtkmm-2.4-1v5 libimage-magick-perl libimage-magick-q16-perl libkdewebkit5 libkexiv2-11v5 libkexiv2-data

  libkgeomap-data libkgeomap2 libkhtml5 libkparts4 libktexteditor4 libkvkontakte1 liblensfun-data liblensfun0 libmagick++-6.q16-7 libmarblewidget-qt4-22 libmediawiki1 libpotrace0

  libqtsolutions-soap-head1 libqtwebkit4 libquazip1 libvisio-0.1-1 libwlocate0 marble-qt4-plugins python-appindicator python-crypto python-gconf python-gobject python-keybinder python-numpy
  python-prctl python-scour python-xdg python3-scour scour

Use 'sudo apt autoremove' to remove them.

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Not sure if these packages were all installed automatically.

---

### Post by Perfect Storm on 2018-08-31
But can you install Inkscape now? Try that.

---

### Post by stinktier2 on 2018-08-31
> **Artificial Intelligence said:**
> But can you install Inkscape now? Try that.
Nope. Same problem as before.

---

### Post by Perfect Storm on 2018-08-31
Lets try take the lib that are broken:

```
sudo apt --fix-broken install libgslcblas0
```

---

### Post by stinktier2 on 2018-08-31
> **Artificial Intelligence said:**
> Lets try take the lib that are broken:
```
sudo apt --fix-broken install libgslcblas0
```

That did it! Thank you, I can finally install Inkscape. \\:D/

---

