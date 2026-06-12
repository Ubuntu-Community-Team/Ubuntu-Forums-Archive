---
title: "Upgrade 5.10-6.06 fault"
date: 2006-09-16
forum: Installation &amp; Upgrades
---

### Post by racebit on 2006-09-16
Hey all,
   I'm fairly new to the linux world and I have been using 5.10 ubuntu for about 6 months and love it. I tried 6.06 and like it more than 5.10 and decided it was time to upgrade. I went to the update manager in 5.10 and as soon as I do I get this error message.
"Cannot install all available updates. Some updates require the removal of other software. Use the function, "Mark all upgrades" in package manager or do "sudo apt-get..." etc. Then it says "The following will be skipped."
cpp
cpp-4.0
g++
g++-4.0
gcc
gcc-4.0
libc6-dev
libstdc++6-4.0-dev

So I pressed ok, tried to upgrade, and get "could not calculate the upgrade" error. Any ideas? I think the two are related.
Once again, I'm a linux newb so let me know if my provided info was inadequate.

Thanks Ubuntu community.

---

### Post by linear on 2006-09-16
There is good troubleshooting advice in this thread: [http://www.ubuntuforums.org/showthread.php?t=187656](http://www.ubuntuforums.org/showthread.php?t=187656).

Also take a look at the thread on fixing broken dependencies: [http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672), which could be your problem.

---

