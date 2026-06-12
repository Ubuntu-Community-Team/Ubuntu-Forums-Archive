---
title: "resize partition hangs on install"
date: 2007-10-06
forum: Installation &amp; Upgrades
---

### Post by intellijel on 2007-10-06
I have windows XP pro already installed on a 500gb WD sata drive. 
My system:
Asus commando mobo
2gb OCZ platinum rev2 ram
Intel Q6600 2.4 Ghz quad core

I am trying to install the latest version of Ubuntu into it's own partition on the same drive that windows is on. I boot into the install using the ubuntu  iso burned to a cd. During the install process I choose the guided partition option and then resize it to 50gb. When it starts the resizing process it just hangs at 0%. So far I have waited 30 minutes with no change.

Any idea what's wrong?

---

### Post by logos34 on 2007-10-06
One thing you might try is to run defrag on windows several times to compact your files as much as possible.  If there are any 'unmovable' files (green bars) on the right they may be preventing you from shrinking the partition down to 50GB.  Temporarily disable hibernation (power options) and paging/virtual memory (control panel>system>advanced tab).

Hope that helps.

---

