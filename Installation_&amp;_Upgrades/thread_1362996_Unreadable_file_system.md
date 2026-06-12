---
title: "Unreadable file system"
date: 2009-12-23
forum: Installation &amp; Upgrades
---

### Post by Feilin on 2009-12-23
When I reinstalled my Ubuntu, which was next to another partition for Vista, I couldn't start up Vista. The grub loading screen for choosing OS goes black for an instant and then returns when I try to load Vista. Inside Ubuntu, I cannot even see the file system and according to GParted, the partition is not mounted and unreadable along with a yellow warning triangle. I suspect the reinstallation messed up the grub loader somehow, though I cannot see why it would damage the file system itself. How do I make my partition readable again, if only from Ubuntu so I can save my files?

---

### Post by oakgrove on 2009-12-23
I'd suggest using a live cd and clicking on the drives in your "Places" menu at the top until you find the Ubuntu partition with your files.

---

### Post by Feilin on 2009-12-24
But it's not on my Ubuntu file system, it's on my unreadable Vista ntfs partition. I want to access it from Ubuntu to save my files, so how do I make my partition readable again?

---

### Post by oldfred on 2009-12-24
Both gparted and Ubuntu will not read a windows partition that was not shut down cleanly. Or when windows restarts it will automatically try to run the checkdisk routine to repair itself.

It would be best to let windows run its repairs. Can you try to boot into windows.

There is a way to mount a NTFS partition with a force parameter to mount but it is not recommended except as a last hope.

---

