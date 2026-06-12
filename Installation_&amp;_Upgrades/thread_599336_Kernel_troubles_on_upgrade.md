---
title: "Kernel troubles on upgrade"
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by dotnick on 2007-11-01
The upgrade from Feisty to Gutsy went nearly flawlessly for me; but,  there were still several issues.

1st:  The new kernel hated my computer and would hang while detecting USB devices, etc.

2nd:  Because I couldn't use the new kernel, I resorted to an older one.  But my nvidia drivers and nvidia-glx were too new for the old kernel so I had version mis-matches.  This was resolved by reenstating the feisty repositories so I could go backwards with the kernel version, linux-restricted-modules, and nvidia-glx.  (essentially resolved, but still disappointed with the newest kernel build)

3rd:  Ubuntu seems to be spinning up my hard drive needlessly and I don't know what is doing it.  To anyone reading, would it be an option in the kernel or a user space program doing this (which one?)

4th:  All of my updates error out because it can't set up console-settings and ubuntu-minimal.  Both of these seem to have been installed automatically but I'm unsure of what they are and what they have that I might want.  I beleive ubuntu-minimal is just a meta package.

In conclusion.  The upgrade was easy for me, minus the kernel and graphics driver issues.  I'm also hoping to get to the bottom of the hard drive spinning up frequently.

---

