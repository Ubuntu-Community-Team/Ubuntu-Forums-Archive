---
title: "Upgrading, failed to fetch files?"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by starbase1 on 2010-05-08
I'm trying to upgrade everything on this computer to the release Lucid, and am getting errors retrieving some files, here's a sample of one of the errors, (the rest are very similar)

[B]W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/b/base-files/base-files_5.0.0ubuntu18_amd64.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/b/base-files/base-files_5.0.0ubuntu18_amd64.deb)
  404  Not Found [IP: 91.189.88.31 80][/B]

Anything I can try to fix this?

Nick

---

### Post by kansasnoob on 2010-05-08
Go to System > Administration > Software Sources and check some things.

#1) Under the Ubuntu Software tab be sure that the Cdrom option is NOT checked, also look at the choice of Server - you might **consider changing to Main Server.**

#2) Under the Other Software tab be sure that nothing other than the "Partner" repos are checked.

#3) When you click on Close be sure to click on Reload. If that returns errors go to step #4:

#4) Close Software Sources and open Synaptic. Click on Search and type "keyring" (w/o the quotes) and be sure that both "ubuntu-keyring" and "gnome-keyring" are installed, if not install them, then click on Relaod and see if you still get errors.

---

### Post by starbase1 on 2010-05-08
Many thanks, I did the first three steps as you describe, and all the stuff is being installed as I type!

---

