---
title: "Problem installing HP driver"
date: 2010-09-10
forum: Installation &amp; Upgrades
---

### Post by kjvee on 2010-09-10
error: No output seen in over 300 sec... (Is the CD-ROM/DVD source repository enabled? It shouldn't be!)
error: Package install command failed with error code 255
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ?

I've tried this
[http://ubuntuforums.org/showthread.php?t=1070166]("http://ubuntuforums.org/showthread.php?t=1070166")
but it didn't work for me. My sources.list already had the #.

By the way I'm a new user to ubuntu and I'm having a pretty good time. :)
Almost starting to feel at home in this OS.

edit: I'm sorry. I realized I posted in the wrong section. Would appreciate it if someone would move it to the correct one.
Thanks :)

---

### Post by sydbat on 2010-09-10
> **kjvee said:**
> error: No output seen in over 300 sec... (Is the CD-ROM/DVD source repository enabled? It shouldn't be!)
error: Package install command failed with error code 255
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ?

I've tried this
[http://ubuntuforums.org/showthread.php?t=1070166]("http://ubuntuforums.org/showthread.php?t=1070166")
but it didn't work for me. My sources.list already had the #.

By the way I'm a new user to ubuntu and I'm having a pretty good time. :)
Almost starting to feel at home in this OS.

edit: I'm sorry. I realized I posted in the wrong section. Would appreciate it if someone would move it to the correct one.
Thanks :)Have you tried installing the HP drivers from Synaptic? They are called HPLIP and are pretty close to the most current ones available directly from HP. System > Administration > Synaptic

Unless you need specific support for a specific printer that requires the most up-to-date HPLIP from HP, the one in the repository should be fine (and save you a few headaches).

---

### Post by kjvee on 2010-09-10
Actually the latest HPLIP is what I'm using.

edit:
Ok new problem.
A package manager 'aptitudeinstall--assume-yesbuild-essential' appears to be running. Please quit the package manager and press enter to continue

I don't actually see any windows. I hope HPLIP didn't affect any of the default files.

edit2: OK I think I got it all fixed.

---

