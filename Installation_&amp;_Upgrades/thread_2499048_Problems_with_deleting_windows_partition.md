---
title: "Problems with deleting windows partition"
date: 2024-07-09
forum: Installation &amp; Upgrades
---

### Post by borisaurus15 on 2024-07-09
Recently, my Windows operating system has been experiencing frequent crashes, initially occurring approximately every 30 minutes, but now happening as frequently as every 3 minutes, accompanied by a "Memory Management" error. Consequently, I have opted to transition back to Linux. However, I am encountering difficulties when attempting to delete the Windows partition. This issue persists whether I attempt deletion using the setup programs provided by Windows, Ubuntu, or  even the GParted app, despite ensuring that the partition is unmounted.

Attempts to resolve the issue through the Windows Automatic Repair feature have proven unsuccessful. Similarly, efforts to access Safe Mode have been futile; even after holding shift while im selecting to turn it off and click on "restart on safe mode" it doesnt open.

I seek advice on how to successfully delete the Windows partition and proceed with installing Linux without encountering these persistent obstacles. Any guidance or suggestions would be greatly appreciated.

---

### Post by borisaurus15 on 2024-07-09
Btw more on the gparted thing, whenever i delete the partition it just reappears again. Whenever im in windows and try to delete apps they also reappear again after the crash for no reason

---

### Post by ubfan1 on 2024-07-09
Might be a final command to "write changes to disk" which would actually make the changes in memory go to the disk.

---

### Post by Rubi1200 on 2024-07-09
Sounds like a failing hard drive to me.

Have you run any checks to confirm whether this might be the case?

---

