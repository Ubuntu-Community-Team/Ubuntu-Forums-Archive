---
title: "fixmbr - fdisk /mbr"
date: 2005-10-09
forum: Installation &amp; Upgrades
---

### Post by da_unruled on 2005-10-09
I have a dualboot pc with ubuntu on one partition and windows on the other. Grub is the bootmanager. I want to get rid of ubuntu because its broken and using 5gb space which I need/can use for windows.

Ive heard of fdisk/mbr and Ive heard of fixmbr....which one should I try?
is there any risk involved? if I lose my winxp data I am fried...

---

### Post by Hairy_Palms on 2005-10-09
if theres any risk always backup but you should be able to fix the mbr

---

### Post by da_unruled on 2005-10-09
right, but which of the two commands? fdisk/mbr? (and how would I access that), or the fixmbr command?

Im just not sure if there's a difference between the 2..

---

### Post by otherworldbob on 2005-10-11
If memory serves, 'FixMBR' is what you want. :) 

I used this after a bodged Fedora install, and was able to get back into Windows, rather than a Spanish error message about a non-existant floppy disc.

I think the two commands serve the same purpose, but 'fdisk /mbr' is older, whereas 'fixmbr' is on the XP install CD in the recovery console.
Though don't hold me to that!

Good luck, just remember to backup anything super important incase I've given you duff advice.

---

