---
title: "Installation failed halfway"
date: 2008-01-31
forum: Installation &amp; Upgrades
---

### Post by Enigmaman on 2008-01-31
Trying to install Ubuntu  but it keeps freezing at 44%.  have checked the disk and one file is damaged. 

I take it I need to burn a new CD?

If so, how do I do that as I cannot boot into Windows.

---

### Post by Pumalite on 2008-01-31
Use your Installation CD to fix MBR. Recovery>FIXMBR>FIXBOOT. If you dont have an Installation CD, use Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Then, follow this guideline:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

---

### Post by reckless2k2 on 2008-01-31
i assume you were trying to do the dual boot action? you will need another disk. to get back to windows you need to fix the master boot record. do you have your windows cd by chance or was this an OEM?

---

### Post by shad0w_walker on 2008-01-31
You could try booting the LiveCD, downloading the ISO in that and then burning it to disc whilst there. You should be able to force the cd drive to eject, just make sure you have run the programs you need to access before you remove the disc (So they are in memory and still usable)

---

