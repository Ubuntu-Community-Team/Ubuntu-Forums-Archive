---
title: "dpkg hangs, can't --configure"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by Smart Bookmarks on 2008-05-03
Upgrading from 7.10 to 8.04, everything progressed smoothly until the Update Manager tried to install openoffice.org-writer2latex, at which point the Update Manager started to hang. I left it overnight (~8 hours), figuring it was just a complicated procedure that would take a while, but it was still stuck trying to configure openoffice.org-writer2latex. 

I killed the Update Manager and tried to run it again, but the system told me dpkg was interrupted and I needed to run dpkg --configure -a. I did so, the system started to hang while trying to configure openoffice.org-writer2latex.

I tried removing openoffice.org-writer2latex with the dpkg --remove openoffice.org-writer2latex command, dpkg continued to hang during this procedure. Tried purging with dpkg --remove -a, system continued to hang. No matter what I can't seem to get rid of this program, which, in a slice of irony, I have no intention to use. Seriously, I've never even used LaTeX or Writer. I'm an AbiWord user. How can I resolve this and proceed with the upgrade? apt-get install -f did nothing, as it seems to depend on dpkg to run.

---

### Post by halalkebabhut on 2009-08-22
yup same problem here with 9.04

---

