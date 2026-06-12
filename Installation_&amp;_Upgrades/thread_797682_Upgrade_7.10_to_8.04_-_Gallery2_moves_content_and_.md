---
title: "Upgrade 7.10 to 8.04 - Gallery2 moves content and fills /var"
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by Krodren on 2008-05-17
Hi everyone.  This has been bugging me since yesterday.  I upgraded my 7.10 server using do-release-upgrade.  Part way though it would die complaining that there was no available space in the destination.  df showed that the /var partition (2GB) was full to the brim, so I went in and cleared the package cache (apt-get clean) and tried again.  It died in the same spot.  Now in searching /var, I see that /var/lib/gallery2 is filled with pictures.

Originally, I had gone through the steps to move the gallery picture repository to /usr/share/gallery2 which is on a much larger partition.  For whatever reason, as part of the upgrade, gallery2 decided to start moving that content back to /var/lib/gallery2

I moved the new /var/lib/gallery2 to a different partition temporarily, as it had pictures that were now removed from /usr/share/gallery2 and restarted the upgrade.

I ended up hitting ctrl-c during the part where it started the move and it only canceled the gallery2 upgrade and finished with the rest.  The system appears to be fine otherwise.

I never saw any option or anything to prevent it.  I'm still not sure I have all the pictures or not.

Anyway, figured a support message might help out someone else.

-Jeremy

---

### Post by Krodren on 2008-05-17
It looks like during the upgrade /etc/gallery2/config.php was updated and points back to the new /var/lib/gallery2 path.  I don't remember seeing it ask me to replace it during the upgrade, but it might have.  (I do try to be careful, but who knows.)

Even so, I wouldn't think it should move those pictures without asking or at least checking for available space before doing so.

After mucking with it and without knowing if I screwed up any pictures in the upgrade/cancel thing, I'm in the process of copying the backup folder of the gallery into a clean install of gallery2.

Good luck to anyone else with this problem! :)

---

