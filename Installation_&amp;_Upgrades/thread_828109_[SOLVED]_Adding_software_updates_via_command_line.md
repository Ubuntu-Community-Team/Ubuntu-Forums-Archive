---
title: "[SOLVED] Adding software updates via command line"
date: 2008-06-13
forum: Installation &amp; Upgrades
---

### Post by ktechman on 2008-06-13
I got so far using sudo aptitude from the terminal and searching for packages that the update manager reports "not all updated can be installed" then I hit a snag, it asks for the new package grouping mechanism??????? Any love out there today?
[ATTACH]73928[/ATTACH]

---

### Post by avtolle on 2008-06-13
From terminal[code sudo aptitude update && sudo aptitude safe-upgrade[/code] will upgrade you to what can be upgraded. From the screenshot, there is a dependency listed there which will not permit the installation of the packages you request.

---

### Post by ktechman on 2008-06-13
Thank you. Just for my info is the "red" area the problem conflicting with another package?

Regards

---

### Post by avtolle on 2008-06-13
From looking at the screenshot you posted, the -xine file depends on amarok being installed; but as I read it, installing amarok will break the system (admittedly, just gave it a quick read).

---

### Post by ktechman on 2008-06-13
Amarok is installed and this is an update apparently. I upgraded one package(Lyricue) and it wiped my MSQL database, hated that one, but I am still learning here. Why would it say I needed Amarok if it is already installed? I do have backports listed on my software sources list, would that make the difference or be the key to my question.

---

### Post by avtolle on 2008-06-13
Do you also have the "proposed" repository enabled? If so, it (Amarok) may be being put out there for testing. In any event, you can uncheck the backports repository (and the proposed one as well) in your software sources list, reload the same, and see if there's still an upgrade to Amarok being offered.

---

### Post by ktechman on 2008-06-13
That worked but I am at a loss as to why when the same updates are showing for amarok?

---

