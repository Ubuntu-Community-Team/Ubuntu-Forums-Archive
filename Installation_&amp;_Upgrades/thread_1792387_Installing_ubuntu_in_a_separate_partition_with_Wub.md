---
title: "Installing ubuntu in a separate partition with Wubi"
date: 2011-06-28
forum: Installation &amp; Upgrades
---

### Post by ktp.kti on 2011-06-28
I am trying to install ubuntu in a separate partition (I have tried it and now i love it!). I have a doubt. If i install ubuntu with wubi in the new partition, will ubuntu get uninstalled/damaged when the partition containing windows is formatted. I think this is expected as wubi installs ubuntu as an uninstallable windows program. Am i right?

---

### Post by Mark Phelps on 2011-06-28
One of the main reasons for using Wubi is to AVOID having to create a separate partition space for Ubuntu.  Since you've already done that (apparently), there is no real point in using a Wubi-based installation.

---

### Post by dFlyer on 2011-06-28
If you install wubi, and then delete/repartition your windows install you will loose the wubi install along with the windows install. If you have a ubuntu partition separate from windows and decide to delete your windows partition, ubuntu will still be there. You may need to update your grub2 to remove windows.

Wubi runs from within windows. A dual boot install runs as a separate OS from Windows.

---

### Post by ktp.kti on 2011-06-28
Thank you Gary!

---

