---
title: "Evolution 2.32.2 in Ubuntu 11.08"
date: 2011-11-23
forum: Installation &amp; Upgrades
---

### Post by showe1966 on 2011-11-23
Just spent a few hours searching for this answer so I have decided to post it.
I hupgraded to Ubuntu 11.08 recently and that included Evolution 2.32.2.
Evolution still gives problems of syncing mail folders if you have vast quantities of mail (as I do) .
Every now and again , one of the mail folders gets corrupted so it gives you an error message "Failed to store folder - mismatch" or something like that.

Anyway, to fix this problem, you need to do the following:-

1. Completely stop evolution with the command
evolution --force-shutdown

2.delete or rename the folders.db file.
3. Restart evolution.

Anyway, I couldn't find the location of this file anymore in the new version.
After a few hours of frantic searching , I discovered that the folders.db file is now here:-

/home/your home folder name/.local/share/evolution/mail/local/

So there you have it. QED etc.
Great isn't it ????

---

### Post by LinuxFan999 on 2011-11-23
You can try a different email client, like Thunderbird, and remove evolution.

---

