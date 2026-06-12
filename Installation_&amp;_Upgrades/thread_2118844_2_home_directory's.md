---
title: "2 home directory's"
date: 2013-02-22
forum: Installation &amp; Upgrades
---

### Post by boregard on 2013-02-22
Hello, I have a quick question. after reinstalling 12.04 I now have a HOME dir and a home dir. under my old username. Can someone please explain why? Thanks so much.

---

### Post by offgridguy on 2013-02-22
> **boregard said:**
> Hello, I have a quick question. after reinstalling 12.04 I now have a HOME dir and a home dir. under my old username. Can someone please explain why? Thanks so much.
Did you have a separate home, with the previous installation?

---

### Post by boregard on 2013-02-22
No, I just had one. I thought when I reinstalled everything from old install would be deleted. Thanks for reply

---

### Post by grahammechanical on 2013-02-22
Did you mark the partition to be formatted? Then the re-install would install over the existing installation but not remove old folders. If you had kept the same username you would have found that your previous settings would still be in place.

Then again, you could be confused by the fact that there is always at least two home folders. There is a Home folder in the File System/Computer part of the system file structure and inside that Home folder there is the home folder that has our username on it.

The file manager calls our username folder - Home. But when we look into File System (Computer for 12.10) we see another Home folder.

Regards.

---

### Post by boregard on 2013-02-22
> **grahammechanical said:**
> Did you mark the partition to be formatted? Then the re-install would install over the existing installation but not remove old folders. If you had kept the same username you would have found that your previous settings would still be in place.

Then again, you could be confused by the fact that there is always at least two home folders. There is a Home folder in the File System/Computer part of the system file structure and inside that Home folder there is the home folder that has our username on it.

The file manager calls our username folder - Home. But when we look into File System (Computer for 12.10) we see another Home folder.

Regards. cant remember if I marked it for formatting or not. but i backed up all the files i wanted to keep & put them back on new install. now i have those, plus the old ones on home john old username. wonderin if i can just delete ones named john?

---

