---
title: "Upgrade Problem from 8.04 to 8.10"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by dethredic on 2008-11-02
So, it is on the like fetching packages step or something like that (third one). It has downloaded 851 of 13xx. Then I get this error:


> Could not download the upgrades
The upgrade aborts now. Please check your Internet connection or installation media and try again. All files downloaded so far are kept.
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/h/human-icon-theme/human-icon-theme_0.30.2_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/h/human-icon-theme/human-icon-theme_0.30.2_all.deb) Unable to connect to ca.archive.ubuntu.com http:
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines-murrine/gtk2-engines-murrine_0.60.1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines-murrine/gtk2-engines-murrine_0.60.1_i386.deb) Unable to connect to ca.archive.ubuntu.com http:
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-gdm-themes/ubuntu-gdm-themes_0.30_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-gdm-themes/ubuntu-gdm-themes_0.30_all.deb) Unable to connect to ca.archive.ubuntu.com http:

Those were only like the first 5 or so of like well, I guess 13xx-851.
As far as I can see they are all ca.archive.ubuntu.com.

**[SIZE="3"]OK, THE ABOVE IS FIXED. NEW PROBLEM BELOW.[/SIZE]**

When I boot up I get this error:

kernel panic : not syncing; VFS; Unable to mount root fs on unknown-block

anyideas?

---

### Post by Peter09 on 2008-11-02
I suspect that site is overloaded or down. Try a different mirror.

---

### Post by SiO-Buntu on 2008-11-02
I believe I found an easy way to fix this.

Simply go to System/Administration/Software Sources.
In the Ubuntu Tab, change the "DOWNLOAD FROM" to "MAIN SERVERS".

Mine was set to CANADA... I beleive that was my problem.

---

### Post by dethredic on 2008-11-02
> **SiO-Buntu said:**
> I believe I found an easy way to fix this.

Simply go to System/Administration/Software Sources.
In the Ubuntu Tab, change the "DOWNLOAD FROM" to "MAIN SERVERS".

Mine was set to CANADA... I beleive that was my problem.

This fixed it. My download speed also increased!

Thanks.

EDIT:

When I boot up I get this error:

kernel panic : not syncing; VFS; Unable to mount root fs on unknown-block

any ideas?

---

