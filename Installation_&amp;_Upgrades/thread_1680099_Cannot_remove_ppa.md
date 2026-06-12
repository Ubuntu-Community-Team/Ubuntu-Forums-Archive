---
title: "Cannot remove ppa"
date: 2011-02-02
forum: Installation &amp; Upgrades
---

### Post by Brown Betty on 2011-02-02
I am having a slightly ridiculous problem where a ppa added cannot be removed.

The akirad repository, (deb [http://ppa.launchpad.net/akirad/akirad/ubuntu](http://ppa.launchpad.net/akirad/akirad/ubuntu) maverick main) 404s, because, I assume, it does not have a maverick version, and causes my update manager to repeatedly inform me my sources are outdated, because it cannot be reached.  Because I do not care one way or another about the repo, I attempted to remove it by deleting the sources.list.d/akirad.list* files.  They magically reappeared.

I then tried visiting Synaptic -> Settings -> Repositories -> Other Sources, and selecting and deleting the akirad entries that way.  Wooh, they have disappeared from /etc/apt/sources.list.d/!

And yet, the next thing I know, I am being told that akirad has 404ed, and my source list is out of date.

It seems that the repo is added again every time I reboot, but I only know that that's when I *notice* it.

Does anyone know what's going on, or how to stop it?

---

### Post by garvinrick4 on 2011-02-02
Open a terminal and:
```
gksudo gedit /etc/apt/sources.list
```Put a # (comment sign) in front of line that is offending
and hit save. Will now not recognize line.

---

### Post by Cattle on 2011-03-18
The issue of reappearence of the Akirad Repository even after it has been deleted from the etc/apt/sources.list.d seems similar to that of :

[http://ubuntuforums.org/showthread.php?t=1703618&highlight=Akirad](http://ubuntuforums.org/showthread.php?t=1703618&highlight=Akirad)

The ppa reappears after a re-boot seems to be due to the 'akiradrelease' script running at every boot-up of the system. FYI, the 'akiradrelease' script should be located at etc/init.d/.

Try running via terminal :

locate akirad

If the output has the 'akiradrelease' at etc/init.d/akiradrelease , try to remove that script file from that folder to another non-File System folder, and then delete any akirad ppa at etc/apt/sourceslist.d.

Reboot and then check whether the ppa reappears.

Best Regards:)

---

### Post by JohnMcReynolds on 2011-04-12
Yipee!  Removing the script did the trick.  Many thanks for the post.

---

