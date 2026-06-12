---
title: "Unable to report bug with Alternate CD upgrade"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bsmith1051 on 2009-10-26
I believe this is actually a long-standing bug and I'd assumed it would've been fixed by now?

I am running Ubuntu 9.04 (i386) and downloaded the 9.10 Alternate CD.  I then initiated a 'local' upgrade using the CD.  So far, so good, even after stopping and starting the upgrade twice; in the past this has confused the update-manager.

The problem is that I selected NOT to download additional updates but it's still doing it.  So what should have been a relatively quick upgrade has now dragged-on for over 2 hours.

P.S.  I tried to report this on Launchpad but I can't find a link for Report Bug anymore?

---

### Post by humphreybc on 2009-10-26
Hmm, that's odd. I upgraded to Karmic on Sunday night using the alternate CD, locally mounted in Jaunty. I opted to not download updates and sure enough, it didn't download extra updates, just installed the packages off the CD image. (Which, by then, were out of date, so I had another 300mb of updating to do later on!)

---

### Post by bsmith1051 on 2009-10-27
So, even just a few days later there were already 300 MB (nearly half the original files) worth of updates??  I suspect the real problem, then, is that if you cancel the upgrade then the settings are not fully reset.  I had originally started the upgrade and answered 'Yes' to download because I'd assumed there wouldn't be anything to download.  When I saw that there were -- a lot! -- I cancelled and tried to restart it with 'No' for downloads.  But instead it continued trying to download.  Eventually I just gave up and let it do the full download/update and it seems to have completed successfully.

---

