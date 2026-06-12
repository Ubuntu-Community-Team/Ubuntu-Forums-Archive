---
title: "Broken 10.04 update"
date: 2010-03-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by DJ . on 2010-03-28
I installed updates for 10.04 in update manager and one update gave me an error (the update was mythbuntu-gdm-theme (new install) and the error was 
E: /var/cache/apt/archives/mythbuntu-gdm-theme_0.5-0ubuntu1_all.deb: trying to overwrite '/usr/share/images/xsplash/logo_small.png', which is also in package ubuntu-xsplash-artwork 0) I ignored this and whenever I try to install something new from ubuntu software center I get a message saying that I have one broken package. How do I stop this?
I searched mythbuntu in ubuntu software manager and i get Mythbuntu-default-settings installed. I don't want to screw up my computer (yet) so I left it installed. Will uninstalling this get rid of that annoying message?

---

### Post by colobix on 2010-03-28
I rad about this bug in the list over known bugs in beta 1.
If you updated to 10,04 for testing you should have installed it on its own partition instead. However, they will address this bug in the beta 2 release.
Anyway, upgrading from a version that works perfectly to a beta 1 version of a not yet released version is just stupid, and you have only yourself to blame for it.

---

### Post by bobcollard on 2010-03-28
A bit harsh. colobix. 
DJ,  Read the instructions before you update or upgrade anything.  Burn the Live CD and test it from that, or use Virtual Box.  Keep a working system on your drive at all times for everyday use, or, writing to the forum for help.  Above all **Back Up** everything you value.

---

### Post by lidex on 2010-03-28
Try synaptic in administration menu. Select "Custom Filters" below-left, then "Broken" above-left. In right pane right-click package and select "Mark for complete removal". Now click the apply button in toolbar.

---

### Post by Arand on 2010-03-29
See: [https://bugs.launchpad.net/ubuntu/+source/netbook-meta/+bug/550237](https://bugs.launchpad.net/ubuntu/+source/netbook-meta/+bug/550237)
and/or: [http://ubuntuforums.org/showthread.php?p=9042402](http://ubuntuforums.org/showthread.php?p=9042402)

- Arand

---

