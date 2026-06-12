---
title: "Update pakage ubuntu"
date: 2006-06-15
forum: Installation &amp; Upgrades
---

### Post by Mabkhout Thami on 2006-06-15
when i start my cumputer, ubuntu request me if i want to apdate my system, when i accept the system execute synaptic and if i chose instal update i see this error:

W: Impossible de localiser la liste des paquets sources [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) breezy/main/Packages Packages (/var/lib/apt/lists/fr.archive.ubuntu.com_dists_breezy_main_Packages_binary-i386_Packages) - stat (2 Aucun fichier ou répertoire de ce type)).

excuse me my english is not very good
thinks

---

### Post by ajgreeny on 2006-06-15
Try to removing the fr. from the line in your /etc/apt/sources.list file.

First backup the file in case it all goes wrong by typing in a terminal:-
sudo cp /etc/apt/sources.list /etc/apt/sources.backup

Then type:-
sudo gedit /etc/apt/sources.list
Remove the fr. from the line shown in the error message, save the file and try again with synaptic.

From what I've seen in these forums, some of these localised repositories can be a problem.  I do not know about this one but it is worth trying.

---

### Post by welders4linux on 2006-06-15
I would think that the package/file it is trying to download is unavailable at that location.

perhaps add a few more depositories,

**In English the tree would be:**

System - Administration - Synaptic Package manager - Settings-Depositories

---

