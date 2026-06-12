---
title: "How to roll back individual package upgrades with Synaptic"
date: 2008-02-10
forum: Installation &amp; Upgrades
---

### Post by hushp1pt on 2008-02-10
I want to be able to roll back (un-do) individual package upgrades that I just installed with Synaptic (or similar). For example, if I look up "History" in Synaptic, I see entries like this 

Upgraded the following packages:
kwin-kde4 (4:4.0.1-0ubuntu1~gutsy1~ppa1) to 4:4.0.1-0ubuntu2~gutsy1~ppa1)

I want Synaptic to un-do that upgrade and restore kwin-kde4 (4:4.0.1-0ubuntu1~gutsy1~ppa1), and also un-do any other package upgrades that happened at the same time because of dependencies.  

I imagine Synaptic creates some kind of backup files when it does a package upgrade?   So, can I just use those backups to roll back an upgrade I don't like? 

I have seen Force-Version and it does not seem like an "un-do".   It seems more like an all-purpose "Install" which lets you select any package version available on the package repositories.  There seems to be no connection to the upgrade History on my machine.  Once I tried to do the equivalent of an un-do with Force-Version, but the package version I had in my system (before I upgraded) wasn't available in Force-Version.  But maybe I just don't understand how Force-Version works. 

I am depending more and more on my Kubuntu 7.10 system, and I think I cannot continue to experiment with optional upgrades that I don't really need and which might cause trouble.  For example, every time I upgrade anything in kde4, my cursor in rdesktop turns into a useless square thing- even though I mostly use kde3 and not kde4. Fortunately the rdesktop cursor goes back to normal by itself, after a restart or two- or it has up to now, anyway. 

Thanks-

---

### Post by varnil on 2008-02-10
to the best of my knowlege what you ask is impossible...

---

