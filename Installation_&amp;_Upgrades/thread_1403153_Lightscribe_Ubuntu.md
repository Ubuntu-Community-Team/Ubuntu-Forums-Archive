---
title: "Lightscribe Ubuntu"
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by Martlaro93 on 2010-02-09
I am trying to install Lightscribe on my cpu but it always says "/tmp/lightscribe-1.18.8.1-linux-2.6-intel-1.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences." while downloading. How do i fix that?

---

### Post by NFblaze on 2010-02-09
Sounds like you are using Firefox, but you are selecting to open the program.

Unfortunately I'm in Windows (fixing someones computer) right now, but if you go to Edit > Preferences > Content there should be a way for you to change the content/program associations. '.debs' should be opened with the program called GDebi, but I dont know the actual command name.

Though, in reality you could just choose to 'Save' it to the desktop. Then double-click on it, and it will open appropriately.

---

### Post by murderslastcrow on 2010-02-10
Yeah, save it to the desktop (or wherever you feel most comfortable) and run it with the standard double-click.

Package manager doesn't show up in the Preferred Applications box, but you can easily change it by right-clicking the installer you're using, going to Properties, Open With, and select GDebi from the list of applications.

---

