---
title: "Lost Firefox bookmarks after upgrading to 21.10"
date: 2021-10-16
forum: Installation &amp; Upgrades
---

### Post by jeff-macaud on 2021-10-16
I assume it's because of the migration to snap. Shouldn't upgrade process handle such migration?
Any recommendation to recover them without going back to deb version?

---

### Post by Dennis N on 2021-10-16
If you did not do a new install, you may still have the old Firefox, it just may not be showing in the dock. Look in Applications menu > Internet where you might see two icons. Also, a search for Firefox in Overview screen would show both icons.

---

### Post by tea for one on 2021-10-16
You can still import your bookmarks into the new Firefox snap version.

History > Show All History > Import and Backup > Restore > Choose File

---

### Post by philhughes on 2021-10-16
Your profile should have been migrated [1]. If your old profile is still there, you should be able to copy it into ~/snap/firefox

[1] [https://www.reddit.com/r/Ubuntu/comments/q89ir6/ubuntu_2110_has_landed/hgpja3e/](https://www.reddit.com/r/Ubuntu/comments/q89ir6/ubuntu_2110_has_landed/hgpja3e/)

---

### Post by philhughes on 2021-10-16
I just updated one PC that had 3 Firefox profiles, and all were migrated to the snap when I started Firefox. The actual directory for the profiles is:

~/snap/firefox/common/.mozilla/firefox

---

### Post by vanadium on 2021-10-17
If you are only concerned about the bookmarks, copy your ~/.mozilla/firefox/########.default-release/places.sqlite (## is a random string) to the profile of the snap version under /snap/firefox. Still, I would indeed expect that your profile should have been migrated automatically.

---

