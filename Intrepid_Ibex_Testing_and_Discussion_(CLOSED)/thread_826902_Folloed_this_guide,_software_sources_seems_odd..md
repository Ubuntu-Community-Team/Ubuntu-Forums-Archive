---
title: "Folloed this guide, software sources seems odd."
date: 2008-06-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by philinux on 2008-06-12
[http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_upgrade_from_Hardy_Heron_to_Intrepid_Ibex_.28for_developers_and_bug_reports_only.29](http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_upgrade_from_Hardy_Heron_to_Intrepid_Ibex_.28for_developers_and_bug_reports_only.29)


Everything is in third party software and the Ubuntu software tab shows nothing ticked. Is this normal?

---

### Post by Raptor45 on 2008-06-12
That guide is kinda poorly written, and can lead to giving you broken packages right now with the dist-upgrade.

I would suggest this instead. Get a fresh install of Hardy (don't update), edit /etc/apt/sources.list with a text editor and replace "hardy" with "intrepid". Then update with the update manager, but avoid doing a partial or dist-upgrade. You can then go into synaptic and figure out which further updates can safely be installed; as a general rule packages which only want to install other packages on updating are fine, but avoid packages which want to remove others. Last I checked evolution and apt were the troublesome ones.

(Note: debconf gave me issues the last time I tried. Just uncheck it in update manager, update everything else, then try installing it again.)

---

### Post by Eclipse. on 2008-06-12
> **Raptor45 said:**
> <snip>Then update with the update manager, but avoid doing a partial,
</snip>


Partial update at this time if a release schedule are normal and fine.

---

### Post by philinux on 2008-06-12
Got hardy in a guest on Vbox. 

Doing as suggested still leaves the software sources with all third party and no ticks in Ubuntu software.

I have a snapshot to return to. Before changing the sources.list

edit, update manage failed.

Marked debconf as force version

Doing partial upgrade

Sorted debconf.

It says now ubuntu-desktop cant be installed yet it is?

---

### Post by philinux on 2008-06-12
Upgrade - everything stable after a reboot.

501 upgraded.
89 upgrades held back.

---

### Post by Raptor45 on 2008-06-12
> **Eclipse. said:**
> Partial update at this time if a release schedule are normal and fine.

Partial upgrade will cause things to be removed as dependencies aren't yet met. (Right now evolution will be messed up.)

---

### Post by Eclipse. on 2008-06-12
Evolution working fine with me, there was some changes made with the packages if I remember however.

I havent booted my intrepid partition in about a week now though.

---

