---
title: "Dependency issue: linux-image-generic packages want linux-firmware?"
date: 2008-10-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Mr. Picklesworth on 2008-10-15
With the latest updates, the linux-generic metapackage was automatically removed because linux-image-generic could not be updated. Here is the error:

```
linux-image-generic:
 Depends: linux-firmware  but it is not installable
```

A quick search tells me that linux-firmware is nonexistent. Strange bug to have at this point in the game (given that packages are dead easy to test before deploying, and testing kernel packages is a given), so could anyone confirm this?

---

### Post by psyke83 on 2008-10-15
This is something you should expect from the development release. A package has been uploaded to the repository, and cannot be installed until its own dependencies are added.

Just wait, and don't force any packages.

Edit: This is the pending package: [https://lists.ubuntu.com/archives/intrepid-changes/2008-October/008775.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-October/008775.html)

---

### Post by Bufke on 2008-10-15
Yes I just got this at the same time my wifi no longer works.  Could be related to [http://ubuntuforums.org/showthread.php?t=948665](http://ubuntuforums.org/showthread.php?t=948665)

Well hopefully when the dependencies are added it fixes my problem

---

### Post by inportb on 2008-10-15
Ah, so that's what's been keeping me from upgrading or dist-upgrading that package. I shall wait.

---

### Post by Mr. Picklesworth on 2008-10-15
Aha, thanks psyke. I just found it pretty odd since the linux-firmware package was not in my list. As that makes clear, it's a new one! :)

---

### Post by plun on 2008-10-15
FYI

[https://lists.ubuntu.com/archives/intrepid-changes/2008-October/008777.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-October/008777.html)

[https://lists.ubuntu.com/archives/intrepid-changes/2008-October/008775.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-October/008775.html)

Double... we will see what comes out fom the building PC..:)

---

### Post by inportb on 2008-10-15
linux-firmware is here! Time to upgrade :)

---

### Post by Mr. Picklesworth on 2008-10-15
Oh boy, my Intel wifi still works *and* the little LED is alive again. Let's see if it survives sleep mode... :)

---

### Post by inportb on 2008-10-15
Aack. Mine didn't even survive standby, but it's fglrx's fault. I should not have been so hasty to put fglrx back on my system. lol.

---

### Post by zoomy942 on 2008-10-15
not showing up for me yet in the updater

EDIT: there they are

---

