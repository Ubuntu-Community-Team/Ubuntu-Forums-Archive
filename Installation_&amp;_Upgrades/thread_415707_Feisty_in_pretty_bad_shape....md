---
title: "Feisty in pretty bad shape..."
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by Ressor on 2007-04-20
I've been running Edgy on my Sony laptop with no problems other than a nightmare with getting the mic to record after installing festival so I tried to do a fresh install of Feisty and had lots of problems.

- The installer thinks my internal IDE disk is SCSI???
- There are errors about mounts failing during the install process.
- After the install completed I couldn't get a terminal to open.  The system would freak out and then bring me back to the desktop with no terminal window every time I tried.

I also tried installing the Ubuntu server on the same laptop and had even more problems.

I guess none of the testers use laptops?

All of this in hopes that the stupid mic recording problem would be fixed with newer alsa and sound files in Feisty.

Any chance a new/usable image with be available soon?

Thanks,
Ressor

---

### Post by cogadh on 2007-04-20
The developers don't really come to the board, so I don't think you'll get an answer to the new/uasble image question, but the SCSI/IDE thing I can answer (it is currently the bane of my existence). The latest version of the kernel that is included in the new Ubuntu handles SATA/PATA communications differently than previous versions. Because of this, standard IDE drives are seen as SCSI, even though they aren't. It's actually not a problem (believe it or not).

As for testing laptops, they definitely test laptops, its just that there are literally hundereds of possible hardware configurations and they can't possibly test all of them.

---

### Post by Ressor on 2007-04-20
I'm so disappointed because I've had such a great experiance with Edgy that I assumed this would be perfect.

Thanks, for the reply though!

Ressor

---

