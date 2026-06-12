---
title: "Hardy unable to/mismounting my external HD?"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by HangukMiguk on 2008-04-27
I'm not even exactly sure what's going on.

Originally, upon first boot of Hardy, my external HD (marked as /dev/sda1 in Gutsy, and supposed to mount at /media/SEA_DISC, and previously written in fstab), was improperly mounted.  term would shoot out that the mountpoint was set to /, and looking at fstab, there honestly wasn't any mountpoint set for my main fs (in fact, fstab was pointing at / as /dev/sda1 as an ext3 FS when it's FAT32 so that I can also use it on Windows systems).

When I would open Thunar, SEA_DISC would still be in the left pane.  If clicked, it would symlink to /media/SEA_DISC_.  The only reason I noticed this was that my music files are on my external, and rhythmbox was auto-removing songs, which happens when my HD isn't mounted.  So, when I noticed the difference in Thunar, I try to point my library to /media/SEA_DISC_/xxx/xxx, and it still doesn't recognize it.

I corrected fstab by setting it back to /media/SEA_DISC, and restarted.  It still does not work.  Whenever clicked on in Thunar, it now points to /media/SEA_DISC__.  When I try to mount in aterm, it gives the following (even after umount /media/SEA_DISC__):

> mount: /dev/sda1 already mounted or /media/SEA_DISC busy

What is wrong?  I've tried everything I can think of.

---

### Post by HangukMiguk on 2008-04-27
Bump: I tried going in and changing permissions for the users group on /media/SEA_DISC, still getting the same error in term, with the same result mounting in Thunar.

---

### Post by HangukMiguk on 2008-04-27
problem solved

I have no clue why Hardy reassigned device numbers on my USB, but my HD is now /dev/sdb1 instead of /dev/sda1 (as was found by checking mtab, which I should've done in the first place).

Quick change to fstab, and everything's working right.

---

