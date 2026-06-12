---
title: "Upgrading to Natty from highly-modified Meerkat.  Advice?"
date: 2011-09-22
forum: Installation &amp; Upgrades
---

### Post by Nutria on 2011-09-22
Hi,

I've been running Meerkat now for a while, because I like GNOME 2.32.  However, now I want to upgrade since (hopefully) all of the kinds have been worked out of Natty and don't want to fall too far behind -current.

Will these 10 PPAs gum up the upgrade?  
```

$ ls -1 /etc/apt/sources.list.d/*list
/etc/apt/sources.list.d/google-earth.list
/etc/apt/sources.list.d/gstreamer-developers-ppa-maverick.list
/etc/apt/sources.list.d/lucid-bleed-ppa-maverick.list
/etc/apt/sources.list.d/maverick-bleed-ppa-maverick.list
/etc/apt/sources.list.d/motumedia-mplayer-daily-maverick.list
/etc/apt/sources.list.d/mozillateam-firefox-stable-maverick.list
/etc/apt/sources.list.d/shiki-mediainfo-maverick.list
/etc/apt/sources.list.d/stebbins-handbrake-snapshots-maverick.list
/etc/apt/sources.list.d/transmissionbt-ppa-maverick.list
/etc/apt/sources.list.d/ubuntu-x-swat-x-updates-maverick.list
```

Should I move them out of the way before upgrading?

Should I deinstall those packages?

---

### Post by Hakunka-Matata on 2011-09-22
Have you considered installing Natty on a separate partition?  Install it there, clean, and add your ppa's one @ a time to see if they work or not.

---

### Post by Mark Phelps on 2011-09-22
Strong +1 for the "separate partition" suggestion ...

This is how I "upgrade" from one release to the next.  In-place upgrades (i.e. overwriting the existing version) have proven to have too many problems afterward. And, until the problems are fixed, the Ubuntu install is "broken" and doesn't work properly.

With a separate install, you can add things one at a time, working at your own pace -- because you still have the "old" working version to use.

---

### Post by Seq on 2011-09-22
> **Nutria said:**
> Should I move them out of the way before upgrading?

The release upgrader will disable them when doing the upgrade. You can re-enable each individually if you like.

---

### Post by Nutria on 2011-09-22
> **Hakunka-Matata said:**
> Have you considered installing Natty on a separate partition?  Install it there, clean, and add your ppa's one @ a time to see if they work or not.

Why would I have an unused partition hanging around?

---

### Post by Nutria on 2011-09-22
> **Seq said:**
> The release upgrader will disable them when doing the upgrade. You can re-enable each individually if you like.

Thanks.  That's just what I needed to hear.

---

