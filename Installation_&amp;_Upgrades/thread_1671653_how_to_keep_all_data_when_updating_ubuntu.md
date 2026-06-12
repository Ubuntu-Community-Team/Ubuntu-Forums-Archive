---
title: "how to keep all data when updating ubuntu?"
date: 2011-01-20
forum: Installation &amp; Upgrades
---

### Post by u-noob-tu on 2011-01-20
this might be a stupid question, but im not sure how updating ubuntu works. my sister has a dell inspiron laptop which came with ubuntu which she got almost 3 years ago and never bothered to update *anything*. she is still using intrepid ibex and has over 800 updates to install (which would take from now until next week to finish). she liked what maverick could do when i showed her my computer but does not want to wait a week to use her computer (im exaggerating, but she doesnt want to wait. she LIVES on her computer). i still have my maverick live cd, but she is extremely concerned about what she might lose data-wise. she has enough pictures to go around the world twice. ive never done an update of ubuntu, just an install of maverick. does ubuntu keep all user data when updating?

---

### Post by JKyleOKC on 2011-01-20
To answer your question, maybe but probably not. Here's the detail:

Her data is all stored in her "home directory" and that directory can be in any of several locations. By default, it's located in /home, which in turn is located in "/" but it's possible during the installation step to mount "/home" in its own disk partition rather than in the same partition as "/" and when that is done, all users' data will be protected during a clean install of a new version, unless you tell the installer to format "/home" at that point in the process.

However since she's been using the system as delivered by Dell, the odds are very great that her home directory is in the main "/" partition and in that case all of her data would be wiped out during a re-install operation.

If you have an external hard disk drive large enough to hold all of her home directory, you could copy the entire directory over to it, then do the installation, and finally copy the critical portions back from the external drive. In addition, when doing the install you could choose "manual" partitioning at that step, and set up a separate partition for "/home" which would provide automatic protection in case of future version upgrades.

It would probably be a good idea, if possible, to invest in a large external hard disk for backup purposes in any event. Prices today are much lower than they were even a year ago!

---

### Post by randiroo76073 on 2011-01-21
I'll agree with JKyleOKC except that making a /home partition in this case is a "must do" to protect personal data/settings. External HDDs are real cheap now, 2tb for about $100 online, it's worth it to protect your data.

---

### Post by theozzlives on 2011-01-21
> **randiroo76073 said:**
> I'll agree with JKyleOKC except that making a /home partition in this case is a "must do" to protect personal data/settings. External HDDs are real cheap now, 2tb for about $100 online, it's worth it to protect your data.

If you don't have the $$$, then see [here]("http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/") to move /home to it's own partition. Regardless, you should backup because the only guarintee you have is that someday your computer _will fail_.

edit: Also, you are upgrading, updates should be done whenever available.

---

