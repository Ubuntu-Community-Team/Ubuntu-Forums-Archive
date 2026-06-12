---
title: "Not getting updates, showing error !"
date: 2011-03-21
forum: Installation &amp; Upgrades
---

### Post by robinsh123 on 2011-03-21
Please let me know that what to do to get the latest updates when my system is showing the error messages after trying to get the updates (on notifications).

_error says_ as below link (a screenshot).

[http://img843.imageshack.us/i/screenshotck.png/](http://img843.imageshack.us/i/screenshotck.png/)
[IMG]http://img843.imageshack.us/i/screenshotck.png/[/IMG]

---

### Post by Dutch70 on 2011-03-21
Have you tried getting the updates through the terminal?

```
sudo apt-get update && sudo apt-get upgrade
```

Other than that working, you're using an alpha version of a development release. Problems should be expected.

---

### Post by robinsh123 on 2011-03-21
> **Dutch70 said:**
> Have you tried getting the updates through the terminal?

```
sudo apt-get update && sudo apt-get upgrade
```Other than that working, you're using an alpha version of a development release. Problems should be expected.

It was working and get upgraded 
about 60% of the available updates.

And showing the same error what to do next ??

current error as follows :-

WARNING: The following packages cannot be authenticated!
  tar libglib2.0-data libglib2.0-dev libglib2.0-bin libglib2.0-0 tzdata xkb-data bash-completion
  brasero-common libbrasero-media1 libpoppler7 libpoppler-glib5 linux-firmware pm-utils poppler-utils
  rhythmbox-plugin-cdrecorder rhythmbox-plugins rhythmbox xserver-xorg-video-geode
  xserver-xorg-video-intel
Install these packages without verification [y/N]? y
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/main tzdata all 2011c-0ubuntu0.10.10
  404  Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2011c-0ubuntu0.10.10_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2011c-0ubuntu0.10.10_all.deb)  404  Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by robinsh123 on 2011-03-22
Please help me !

Now the "Torrent Transmission Client".
is also showing the same error before working.

---

