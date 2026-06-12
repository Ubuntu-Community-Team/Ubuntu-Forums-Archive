---
title: "Installing Programs from CDs"
date: 2006-12-13
forum: Installation &amp; Upgrades
---

### Post by Dragonbite on 2006-12-13
In Edubuntu (Gnome) I noticed that I could add the Kubuntu CD as a repository to update from.

This got me thinking. Since Edubuntu has some programs (Kino, Scribus and Blender) that I usually take hours (dial-up) to download and many of their educational programs are KDE-based I was wondering if I could install just these programs I want from the Edubuntu CD into Kubuntu.

I installed Kubuntu, but I don't know how to set up Adept to pull things from the CD.

All of the CDs are Dapper, shipped from the same time.

If I explore the CD I see the *.deb packages (..../pool/main/) but I don't know what to do with them.

Any help, ideas or "you can't"s appreciated! Thanks.

---

### Post by scrooge_74 on 2006-12-13
you can copy the .deb packages to your pc and use dpkg to install them

you can also tell your repository program (synaptic in gnome) to read from the cd

---

### Post by Dragonbite on 2006-12-13
I saw it in synaptic before, but I want to install into Kubuntu which I have only found Adept as their package manager.

In Adept there is a section to Manage Repositories but it doesn't seem to do something so I'm not sure if I need to point to a specific file?

---

### Post by scrooge_74 on 2006-12-13
I am not to familiar with KDE but in the bottom it should be debian base, so in the repository should be an option to only use the CD.

You can also go to  /etc/apt/sources.list and check which repositories you have, probably the CDs are commentend so as not to use them, you could #everything but the CDs and then update the package list

sudo apt-get update after you insert the CD

---

