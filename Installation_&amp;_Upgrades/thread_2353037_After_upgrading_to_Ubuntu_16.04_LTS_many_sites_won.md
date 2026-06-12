---
title: "After upgrading to Ubuntu 16.04 LTS many sites won't open"
date: 2017-02-18
forum: Installation &amp; Upgrades
---

### Post by jobtmp on 2017-02-18
After upgrading to Ubuntu 16.04 LTS from Ubuntu 14 LTS  cannot open sites except very few. Under Windows can open all sites from the same provider's account. Please advise.

---

### Post by TheFu on 2017-02-18
A quick way to troubleshoot this is to use the guest account login and see if everything works.  If it does, then the issue is with the settings for the browser in your account, not the OS.

You can also try a few different browsers to see if it is 1 or all of them with the issue.  It is is all of them, then you might want to look at ISP/Govt filtering.
* lynx
* chromium-browser
* dillo
* firefox
are a few browsers to try.  Each has different issues and limitations, so be certain you understand those.  For example, dillow doesn't support javascript and doesn't validate HTTPS certificates, but it is extremely fast and lite.

---

