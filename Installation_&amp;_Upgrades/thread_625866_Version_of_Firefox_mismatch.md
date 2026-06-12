---
title: "Version of Firefox mismatch"
date: 2007-11-28
forum: Installation &amp; Upgrades
---

### Post by bkline on 2007-11-28
When I pulled down the latest set of updates for Gutsy this morning, I noticed that one of them was firefox version 2.0.0.10+2nobinonly-0ubuntu1.7.10.1.  I shut down firefox, restarted the app, and brought up Help / About, which displayed 2.0.0.9 as the version.  So I logged out, logged back in, started Firefox, and brought up Help / About, which still displayed 2.0.0.9.  So I rebooted the whole system, logged in, started Firefox, and brought up Help / About, which still displays 2.0.0.9.  Any idea what's going on?

Thanks,
Bob Kline

---

### Post by bkline on 2007-12-17
> **bkline said:**
> When I pulled down the latest set of updates for Gutsy this morning, I noticed that one of them was firefox version 2.0.0.10+2nobinonly-0ubuntu1.7.10.1.  I shut down firefox, restarted the app, and brought up Help / About, which displayed 2.0.0.9 as the version.  So I logged out, logged back in, started Firefox, and brought up Help / About, which still displayed 2.0.0.9.  So I rebooted the whole system, logged in, started Firefox, and brought up Help / About, which still displays 2.0.0.9.  Any idea what's going on?

The package management system pulled down another update for Firefox, which, according to dpkg, is 2.0.0.11+2nobi, but the "About" dialog box still displays 2.0.0.9 as the version of the software.  On a Windows XP box version 2.0.0.11 actually displays the correct version in the About box.  Does no one know what's going on here?  Should I file a bug report?

---

