---
title: "How to upgrade/update offline apt packages."
date: 2022-11-09
forum: Installation &amp; Upgrades
---

### Post by akshay-shar on 2022-11-09
I want to upgrade the apt repository which offline using apt-mirror a month before.
I want to sync/upgrade/update the existing offline apt repository, I don't want to clone complete apt repository again as it 300gb.

Is there any way where we can just download/upgrade/update the delta?

---

### Post by MAFoElffen on 2022-11-13
How I did that in the past was to set up a local repo (server) and do an apt sync... Just saying.

---

### Post by Tadaen_Sylvermane on 2022-11-14
I think apt mirror only does the delta so to speak. It shouldn't re-download anything that hasn't changed. Same way apt will use a package in your local cache if it's the same as what it would download. I could be wrong of course. I mainly just use Squid to cache packages, no local repository.

I'd hope the apt-mirror devs would be smart enough for that and not make you pull the whole damn thing every time.

---

### Post by ActionParsnip on 2022-11-14
Use apt to download all packages for an online system. You can then transfer them to the offline system

---

