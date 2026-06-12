---
title: "Synaptic Package Manager and Lock Version"
date: 2008-09-02
forum: Installation &amp; Upgrades
---

### Post by patricksan on 2008-09-02
I've download the tora source code and after generation a debian file I installed it.

The problem it that now the Update Manager says that I need to update it.

So, what I did: I lock the version. Tora has a red row, but Update Manager continues suggesting me to update it.

What more I can do for eliminate this update request?

Thank you,
Patrick

---

### Post by klrspz on 2008-11-21
I'm having this same problem... Any luck finding a solution?

---

### Post by patricksan on 2008-11-21
No solution!!!

I also stopped to use Tora. I'm using Oracle SQL Developer; and for MySQL, I'm using MySQL Query Browser.

Sorry.

Patrick

---

### Post by martimcfly on 2009-01-03
Same problem here. After manual install of pidgin-plugin-pack, I lock the version for that package in Synaptic but it keeps on showing the "updates available" notification. Any solution?

---

### Post by Mystro256 on 2010-01-20
Found a solution for anyone who cares anymore haha:

For whatever reason you have to use the command line method to hold it for it to properly hold  the version in the update manager

Guide here: [URL="https://help.ubuntu.com/community/PinningHowto#Apt/Dpkg"]https://help.ubuntu.com/community/PinningHowto#Apt/Dpkg
[/URL]

---

### Post by Loevborg on 2010-03-10
Mystro, that was helpful indeed.

What I did is both use the command line version AND the synaptic version. That way, updates using either method don't upgrade the package.

---

