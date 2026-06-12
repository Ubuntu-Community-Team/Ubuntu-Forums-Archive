---
title: "snap-store says an app is proprietary wile is free"
date: 2020-05-15
forum: Installation &amp; Upgrades
---

### Post by corradoventu on 2020-05-15
In snap-store I select an app, the screen says the app is Proprietary while is free, looking at the same app with gnome-software i see is free.
[https://bugs.launchpad.net/snap-store/+bug/1878924](https://bugs.launchpad.net/snap-store/+bug/1878924)

---

### Post by grahammechanical on 2020-05-15
A wild guess would be that the meta data in the snap version is incorrect.

I have installed zoom-client in both deb and snap versions and the snap version crafted by a Ubuntu developer and not the proprietary owner of the software does show the licence for zoom-client as proprietary. With open source software in particular we do not need to rely on the developer creating a snap of their software. Anyone with the skill can create the snap but the person creating the snap would need to be careful about what they list as the details of the app otherwise a software store would provide inaccurate information about the app. This would be my guess as to what has happened.

By the way, the snap store in 18.04 does not have a snap of Synaptic. I will have to check the 20.04 snap store.

Regards.

---

### Post by ajgreeny on 2020-05-15
No, there is no snap for synaptic package manager; it's a .deb install or nothing. 

Or compile it and install it yourself, of course.

---

### Post by corradoventu on 2020-05-15
Both synaptic and pdfchain are .deb packages and can be installed using snap-store, the problem is just the wrong information given by snap-store about the applications.  
The same problem happens with many other .deb packages.
@grahammechanical: both apps are .deb and meta data are correct because gnome-software displays it correctly but snap-store seems unable to correctly interpret the meta data.  
I found the problem in Ubuntu 20.04 and 20.10, don't checked in Ubuntu 18.04

---

### Post by ajgreeny on 2020-05-15
I had not realised that snap-store also listed, and presumably will install .deb packages.  

In fact until about 2 minutes ago I had never even seen snap-store and certainly never used it, and now having seen it I don't think I shall ever bother again.
It seems almost unusable to me with no way that I can figure out how to search for a snap apart from scrolling through huge long lists of packages; have I missed something, ie, a search function in the GUI?

If I want to use a GUI for package management I use synaptic (the champion of GUI package management applications in my opinion), but these days it's more likely to be ***apt*** or ***snap*** in terminal.

---

### Post by corradoventu on 2020-05-16
Snap store (aka Ubuntu Software) is the snap version of gnome-sofware, and can install snaps and (with some trouble) also .deb applications. [https://bugs.launchpad.net/snap-store/+bug/1873040](https://bugs.launchpad.net/snap-store/+bug/1873040)
To search for an app you have the magnifying glass in the top bar.
In Ubuntu 20.04 You can install (by terminal or synaptic) gnome-software which is the a .deb appl and is the well-working version of snap-store.
gnome-sofware has the same icon al snap-store and can install .deb, snap and flatpak.

---

### Post by ajgreeny on 2020-05-16
No magnifying glass icon in my version of snap-store; I spent some time trying to find something like that.

In fact no icons at all, just a typically empty looking gnome-style window, no menus, no icons.

---

### Post by corradoventu on 2020-05-16
On my Ubuntu 20.04 and 20.10 snap-store appears as in attachment, magnifying glass is on top bar left near the mouse pointer.
But if You are using Xubuntu as from Your signature you may be free of covid-snap virus.

---

### Post by ajgreeny on 2020-05-17
Yes. Sorry about that; you're correct and the magnifying glass is there as you said.

All this proves is that I'm a bit of an idiot and did not look carefully enough.  
However, to plead some mitigation, I am not used to the "blank" look of gnome windows with no menus and few if any icons to click on; that's why I missed it.

---

