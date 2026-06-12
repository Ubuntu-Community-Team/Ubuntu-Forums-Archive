---
title: "Recommended vs Proposed upgrades Inconsistency"
date: 2008-06-19
forum: Installation &amp; Upgrades
---

### Post by mauimike on 2008-06-19
I have my "software sources - upgrades" set to important and recommended NOT proposed.

Package manager told me there were updates so I did an update which included an upgrade to 2.6.24-19-server

After re-booting my Virtualbox would not run. After wasting quite a bit of time reinstalling virtualbox through package manager to no avail I discovered that I needed to reset my software sources to "proposed" to get the Virtualbox modules for the 2.6.24-19 kernel. I had a similar experience upgrading to Hardy several weeks ago which killed my Nvidia display and sound. That took the best part of a day to fix.

I can understand the difficulty of keeping all the application and kernel releases synchronized but it is this kind of thing that prevents me from recommending Ubuntu to my wife and friends to replace windows. 

I suspect many Ubuntu users use a VM to run windows apps. so I suggest that Virtualbox and VMware should be considered part of the 'core' Ubuntu and the appropriate drivers/modules be included with 'recommended' updates.

---

