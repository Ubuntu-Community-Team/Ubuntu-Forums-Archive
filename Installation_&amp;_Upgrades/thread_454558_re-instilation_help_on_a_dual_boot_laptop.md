---
title: "re-instilation help on a dual boot laptop"
date: 2007-05-25
forum: Installation &amp; Upgrades
---

### Post by the lemming on 2007-05-25
My laptop has XP and kubuntu on its single 40gb harddrive.  

The laptop had ubuntu until this afternoon when I had a go with KDE after following some advice on another thread.  I was able to sucessfully convert from Gnome to KDE but I have not been able to revert back to Gnome so I have decided to re-insatall ubuntu with Gnome.

Seeing as I have never tried to remove a linux application from a dual boot before I have a coupe of questions.

The first one is, is it a simple matter of putting in the Livee CD and going through the install process again.

or

Do I use the XP Recovery disc to get my Laptop back to one partition before I ever put ubuntu on it

or

Do I do something else?

Cheers

---

### Post by mikewhatever on 2007-05-25
No, you do not need to restore to one partition and then resize again. Just point the installer to the existing partitions by specifying which is root and which is swap, format these partitions only and reinstall. You will loose all data on the partitions you format.

---

