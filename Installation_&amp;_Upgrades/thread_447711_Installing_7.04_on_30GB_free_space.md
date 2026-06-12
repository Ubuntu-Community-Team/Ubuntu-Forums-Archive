---
title: "Installing 7.04 on 30GB free space"
date: 2007-05-18
forum: Installation &amp; Upgrades
---

### Post by alexterm on 2007-05-18
I've downloaded 7.04. On my dual Athlon, dual boot (Mandriva & W2K) PC there is 30GB of free space on hdc6.

An attempt to install MDV2007.1 for evaluation purposes with "use free space" option failed miserably. The MDV installer started nosing around the free space on hda W2K partitions and a 300GB USB external drive (it's there for backup and storage purposes)

Is there any simple method to ensure that 7.04 gets installed on the 30GB partition without affecting the other free areas?

alexterm

---

### Post by Jose Catre-Vandis on 2007-05-18
Best thing to do, or what I do, is create a partition on this free space using the gparted live cd, make sure you identify the correct name/number for the parition, and then select this location when the ubuntu installation asks for one. I only ever use the alternative cd, but I beleive the live cd does offer you a choice. 

This method is a bit clunky, but it always works for me

---

### Post by mikewhatever on 2007-05-18
1. Unplug the external HDD, so that the installer only has one choice and use the 'format drive' option.
2. Create the partitions manually.

---

### Post by alexterm on 2007-05-19
Thanks for the replies.

Concerning manual creation of partitions: I was tripped up by the mounting step. Mounting on / should be sufficient?? I also created a 2GB Swap partition. The last attempt was made with the 300GB drive disconnected.

I did not want to go into detail as another Linux distribution was involved. My main concern was to pick up useful tips for 7.04

Have to keep on trying...

alexterm

---

