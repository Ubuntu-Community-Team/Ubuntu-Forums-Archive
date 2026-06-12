---
title: "apt-get update OFFLINE?"
date: 2011-12-27
forum: Installation &amp; Upgrades
---

### Post by cortman on 2011-12-27
I'm trying to figure out ways to update the APT package lists offline. And thereby update Synaptic as well.
I must say I'm starting to run into dead ends.
To my understanding APT visits a site such as [http://ubuntu.secs.oakland.edu/dists/oneiric/main/binary-i386/]("http://ubuntu.secs.oakland.edu/dists/oneiric/main/binary-i386/") and grabs the "Packages.gz" tarball, which contains a text file with information on all the packages in the repository. Is there some way to redirect apt-get update to a downloaded copy of this text file on the local hard drive?

---

### Post by luvr on 2011-12-27
> **cortman said:**
> Is there some way to redirect apt-get update to a downloaded copy of this text file on the local hard drive?
Downloading a complete software archive, and using that offline, is certainly possible, as I attempted to document [elsewhere on this forum.]("http://ubuntuforums.org/showthread.php?p=7367273#post7367273") You may even want to start at [the first post of that thread,]("http://ubuntuforums.org/showthread.php?p=2100699#post2100699") and follow the links to find further info.

If I understand you correctly, you do not want to download the complete software archives, but only the index files, so that you can keep your package list up-to-date (even though your system won't have the packages themselves available).

I haven't tried that myself, but I believe that you could download just the index files (i.e., the contents of the *"dists"* subdirectory of an online archive), and point your system to that local, downloaded copy, by using a *"file://"* entry in your *"sources.list"* file (cfr. the ***"Wrapping Up"*** paragraph in my post that I refer to above for how to do that). It's not an exact answer to your question, but it should get you started.

---

### Post by cortman on 2011-12-28
Figured it out.

---

