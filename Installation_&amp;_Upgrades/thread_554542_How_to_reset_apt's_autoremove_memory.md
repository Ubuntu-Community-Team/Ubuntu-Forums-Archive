---
title: "How to reset apt's autoremove memory"
date: 2007-09-19
forum: Installation &amp; Upgrades
---

### Post by freedom on 2007-09-19
Since I have too little free space on partition where (K)Ubuntu is installed I tried to free up some space. So I deinstall some Mono icons and Hindu, Japanese and other fonts that I don't need. Naturally, package kubuntu-desktop is removed too since it depends on all of that. But now, apt is suggesting me to do autoremove of practically everything else that belongs within kubuntu-desktop. Is there any way to reset apt's memory so that I can use autoremove function without apt trying to remove packages that I need (want) to stay.
:confused:

---

### Post by schaumkeks on 2007-09-25
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/86921](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/86921) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **freedom said:**
> Since I have too little free space on partition where (K)Ubuntu is installed I tried to free up some space. So I deinstall some Mono icons and Hindu, Japanese and other fonts that I don't need. Naturally, package kubuntu-desktop is removed too since it depends on all of that. But now, apt is suggesting me to do autoremove of practically everything else that belongs within kubuntu-desktop. Is there any way to reset apt's memory so that I can use autoremove function without apt trying to remove packages that I need (want) to stay.
:confused:

This seems to be related to bug report [#86921]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/86921") in launchpad. If you really want to delete packages that the meta-package kubuntu-desktop depends on, you could reinstall all direct dependencies of kbuntu-desktop using the small [shell script provided by Michael Vogt]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/86921/comments/5"). This only marks all installed direct dependencies of those meta-packages as manual installed and should solve your problem.

Because this is fixed during an upgrade to feisty, i assume you are using an older version of (K)Ubuntu.

By the way, the information about whether packages are automatic or manual installed can be found in the file /var/lib/apt/extended_states but you shouldn't modify this manually.

Bye, Sven

---

### Post by freedom on 2007-09-26
Thanks for your reply
Well I am using Feisty, altough it's been upgraded from Edgy so maybe there is some leftovers from it. Anyway, I wil try these solution but I'm also thinking of Gutsy clean install when it came out.
Thanks

---

