---
title: "Still have not been prompted by network manager to a dist upgrade!"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by trjonescp on 2008-04-29
I get gutsy updates, but update-manager doesn't seem to want to upgrade to hardy. This is my sources.list
```

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://us.archive.ubuntu.com/ubuntu/ gutsy-security main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-security main restricted universe multiverse

deb http://packages.medibuntu.org/ gutsy free non-free
```

When I run 'apt-get update' I don't get any errors. Any thoughts?

---

### Post by chewearn on 2008-04-29
Open the update manager, click on the "check" button.  After the check is completed, you should see distro upgrade button on top of the dialog.

---

