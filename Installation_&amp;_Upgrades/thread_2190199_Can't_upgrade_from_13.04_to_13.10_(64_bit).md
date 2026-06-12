---
title: "Can't upgrade from 13.04 to 13.10 (64 bit)"
date: 2013-11-26
forum: Installation &amp; Upgrades
---

### Post by redaxe90 on 2013-11-26
The software updater in my Ubuntu 13.04 64bit system has already notified me of the latest distro release, but when I tell it I want to upgrade, it goes to the upgrade start and prompts me to upgrade or cancel (at the good old notification screen, reminding me of all the things I should read). But after pressing upgrade, it just flashes out and I don't get that upgrade.

Is it possible that I might have to download the entire CD version and install it the old fashioned way or is there a terminal command I can use to force the issue??

---

### Post by ian-weisser on 2013-11-26
Terminal command: **do-release-upgrade**

---

### Post by redaxe90 on 2013-11-26
Thanks, worked like a charm

---

### Post by dunbrokin on 2013-11-27
That does not work for me....it tells me there is no new upgrade...I am definitely on 13.04...and I want to get to 13.11

---

### Post by ian-weisser on 2013-11-27
There is no version called 13.11
Perhaps you mean 13.10?

Please try the command **uname -r** and post the result here.

---

### Post by craig10x on 2013-11-27
If you are running only one ubuntu, then if you run a live iso of 13.10 the installer should give you the option of upgrading (as well as the normal wipe out and replace option)...try that...
It's a lot faster then doing it with the update manager, anyway....
You can read about my experience with it, here:
[http://ubuntuforums.org/showthread.php?t=2181643&highlight=wow+great+upgrade](http://ubuntuforums.org/showthread.php?t=2181643&highlight=wow+great+upgrade)

---

### Post by dunbrokin on 2013-11-27
3.8.0-33-generic

---

### Post by ian-weisser on 2013-11-27
> **dunbrokin said:**
> 3.8.0-33-generic

Try the command **do-release-upgrade**
The command may take an hour or more to complete. It requires reliable network access and reliable power.
DO NOT suspend your system or otherwise interrupt the command while it is running, or you may break your system terribly.
If you get an error message, post the entire session here. Use [code] tags to show output.

---

### Post by dunbrokin on 2013-11-27
Thanks, that worked for me!

i.e. booting from the iso.

---

