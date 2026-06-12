---
title: "Hiding Package updates in Ubuntu Update Manager"
date: 2010-09-03
forum: Installation &amp; Upgrades
---

### Post by James2k on 2010-09-03
I have the package "xvidcap" (Screen recorder) installed in Ubuntu, the problem I have is the version I have installed is an older version and there is a newer version avaliable, but I don't want to install the newer version as this breaks some functionality regarding screen capturing e.g. audio capturing. But each time I run Update Manager the package appears in the list to be upgraded.

Is there anyway to flag the package as do not upgrade or something to make it not appear in Update Manager or at least have it greyed out so the checkbox isn't automatically checked each time update manager is ran?

---

### Post by Tracy177 on 2010-09-03
> **James2k said:**
> I have the package "xvidcap" (Screen recorder) installed in Ubuntu, the problem I have is the version I have installed is an older version and there is a newer version avaliable, but I don't want to install the newer version as this breaks some functionality regarding screen capturing e.g. audio capturing. But each time I run Update Manager the package appears in the list to be upgraded.

Is there anyway to flag the package as do not upgrade or something to make it not appear in Update Manager or at least have it greyed out so the checkbox isn't automatically checked each time update manager is ran?



i have the same problem there are some applications i do upgrade from synaptic and other ones i dont want to upgrade so everytime i want to upgrade something i need to upgrade everything or do it one by one this take time.

---

### Post by thatguruguy on 2010-09-03
Have you tried the "Force Version" option in Synaptic?  It's available under the "Package" menu, or you can just hit ctrl+E.  I believe that overrides the update functionality.

---

### Post by realzippy on 2010-09-03
> **thatguruguy said:**
> Have you tried the "Force Version" option in Synaptic?  It's available under the "Package" menu, or you can just hit ctrl+E.  I believe that overrides the update functionality.

Right.But it is the "lock" version option,not the "force"....

---

### Post by James2k on 2010-09-04
Yeah locking the package does the trick. Thanks guys.

---

