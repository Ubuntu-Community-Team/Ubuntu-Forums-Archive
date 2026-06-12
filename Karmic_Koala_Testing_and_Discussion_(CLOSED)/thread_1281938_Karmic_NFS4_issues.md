---
title: "Karmic NFS4 issues"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by computor on 2009-10-03
Has anyone else had issues with NFS4 in Karmic?  I have my home directory mounted over NFS to an Opensolaris (b124) file server (I actually have two setups like this with the same issue).  Under jaunty used nfs4 w/idmapping without issue.  Ever since the upgrade to karmic (around alpha 3 or so), nfs4 has stopped working.  After logging in usually the desktop will freeze (mouse moves, can't interact with anything).  Sometimes it will hit the desktop and will be fine until I try to open nautilus.  If I launch nautilus from a terminal, it throws an "Eel-critical: eel_preferences..." (I don't have the exact error message -- no way to save it :).

Tinkering with the mount options has no effect (hard,soft,intr,rsize,wsize, etc) and dmesg doesn't have any useful info (other than segfaults/mutex from nautilus et al crashing).  Wireshark also doesn't show anything but normal nfs traffic.

NFS3 works fine aside from having to use nolock due to the init scripts not calling rpc.statd and freezing the boot process.

I've held off on filing a bug report because I'm not quite sure what's happening.  Also, I'm not sure if this is an ubuntu or opensolaris bug--though an ubuntu bug seems more likely.  I booted a jaunty livecd and was able to mount the share just fine.

Just wondering if anyone else had seen this.

---

### Post by SoftwareExplorer on 2009-10-04
Have a look at these, maybe you are having the same problem:
[http://www.ubuntu.com/testing/karmic/beta]("http://www.ubuntu.com/testing/karmic/beta") scroll down to known issues.
[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/431248]("https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/431248") the bug listed on the previous page.

Also, welcome to the ubuntu forums. :)

---

### Post by computor on 2009-10-04
I'm not sure that bug and the behavior I'm experiencing are related.  While I do get the "DNS resolution" errors during startup, everything works fine as long as I use NFSv3 and have nolock enabled on all NFS shares in fstab.  Moreover, that bug seems to have been introduced fairly recently.  I have seen the NFS4 behavior I described in various forms ever since I switched to Karmic (alpha 2 or 3).

---

