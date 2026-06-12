---
title: "Reinstalling ubuntu"
date: 2007-06-30
forum: Installation &amp; Upgrades
---

### Post by Programmerfromthehood on 2007-06-30
Okay so from some reason I'm reinstalling ubuntu today. Anyways, the thing I'm trying to to is just overwrite my old ubuntu partion and just write to there. I'm having so trouble deciding what to do. 

[IMG]http://i70.photobucket.com/albums/i98/LainLover/Screenshot.png[/IMG]
First Pic:
Here you can see that my old partion is there, so do select it and make it a "/" mount point?

Swap data is there too.

[IMG]http://i70.photobucket.com/albums/i98/LainLover/Screenshot-1.png[/IMG]
2nd pic:
Or do I use this guided thing to totally go over hda3(my ubuntu partion) or do I leave this along and try something else?

Thanks in advance!!

---

### Post by logos34 on 2007-06-30
no, don't do the guided.  Notice what the slider says: '100%  42GB'.  But that will set up the new partition on all of the FREE space--leaving 5800 MB of the used space form the old installation.  So what you want to do is go back and choose 'manual' and then delete hda3 and hda5, and create a new ext3 on all of hda3 and a new swap on hda5.  Create a mount point for hda3 at '/' (root) and '/swap' for hda5. Your new install will then overwrite the old on hda3.

---

### Post by Programmerfromthehood on 2007-06-30
> **logos34 said:**
> no, don't do the guided.  Notice what the slider says: '100%  42GB'.  But that will set up the new partition on all of the FREE space--leaving 5800 MB of the used space form the old installation.  So what you want to do is go back and choose 'manual' and then delete hda3 and hda5, and create a new ext3 on all of hda3 and a new swap on hda5.  Create a mount point for hda3 at '/' (root) and '/swap' for hda5. Your new install will then overwrite the old on hda3.[IMG]http://i70.photobucket.com/albums/i98/LainLover/Screenshot-2.png[/IMG]

Is this right?

P.S: Did what you said about deleting hda3 and hda5.

---

### Post by logos34 on 2007-06-30
yep.  that looks right.

---

