---
title: "Openoffice fails after Nov 25th update"
date: 2008-11-27
forum: Installation &amp; Upgrades
---

### Post by kb3lja on 2008-11-27
After Nov 25 update of openoffice 3.0.0-4ubuntu0intrepid1 for x86-64 from ppa.launchpad.net/openoffice-pkgs all openoffice applications fails to start.

---

### Post by HotShotDJ on 2008-11-27
This is a known issue (see: [http://ubuntuforums.org/showthread.php?t=993516](http://ubuntuforums.org/showthread.php?t=993516) )

Open a terminal (Applications --> Accessories --> Terminal) and type```
sudo apt-get remove openoffice.org-gnome
```This should fix you up for now.  Once they correct the problems (in the next few days, one hopes) you can reinstall openoffice.org-gnome.

---

### Post by kb3lja on 2008-11-28
That worked.
Thanks.:)

---

