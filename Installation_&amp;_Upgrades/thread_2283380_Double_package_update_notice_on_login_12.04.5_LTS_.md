---
title: "Double package update notice on login 12.04.5 LTS with different numbers on each"
date: 2015-06-21
forum: Installation &amp; Upgrades
---

### Post by Lido on 2015-06-21
Running 12.04.5 LTS (GNU/Linux 3.2.0-29-generic x86_64). When I log in via ssh, I get this:
```
  Graph this data and manage this system at:
    https://landscape.canonical.com/

5 packages can be updated.
12 updates are security updates.

15 packages can be updated.
12 updates are security updates.

New release '14.04.1 LTS' available.
Run 'do-release-upgrade' to upgrade to it.
```
Should I be concerned? Which is right?

---

### Post by ian-weisser on 2015-06-21
Under the hood a couple things are happening:

First, apt is updating the package database once each day, as part of /etc/cron.daily.
Second, apt does *not* update the package database when you login.
Third, the motd scripts, at /etc/update-motd.d/ , create those messages. The scripts are not perfect under all conditions.

Example: If you login early, before that cron job runs, you will get the results of *yesterday's* update.

Should you be concerned? No. Inaccurate or stale results that have been cached from your last login are annoying, but do not indicate a problem with your system. They merely indicate a bug with the update-motd scripts.

Feel free to wander through those scripts; perhaps you can suggest how to improve them.

Which one is right? Perhaps none of them. New packages can appear in the Ubuntu repositories at any time of the day or night. Just use those messages as a reminder to run apt-get update/upgrade.

---

### Post by Lido on 2015-06-23
Thanks.

---

