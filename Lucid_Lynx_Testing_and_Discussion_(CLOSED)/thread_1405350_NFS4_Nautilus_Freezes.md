---
title: "NFS4 Nautilus Freezes"
date: 2010-02-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by computor on 2010-02-12
Some time ago I had posted that I had been having trouble with NFSv4 mounts after upgrading to Karmic.  Mounts that had been working fine on jaunty freeze when you try to open a mounted directory in nautilus (freezes indefinitely).  I have had this problem on several desktops on both karmic and now lucid.  I have verified this on two different servers--both running opensolaris (they have been upgraded periodically from b112 to b132--the latest).

Mount options don't appear to matter (I'm using hard,intr,tcp, but it also occurs with the defaults).  NFSv3 is fine.  When this first started happening, I seem to recall booting to a jaunty (possibly intrepid) livecd to verify that it still worked.

Once the freeze occurs, I'm unable to unmount the volume (without -l).  Fuser shows that gvfs-gdu-volume is holding a lock on the volume.  Killing this process (what is it? Something to do with gvfs apparently, but I don't see this binary anywhere) causes everything to work normally until reboot.  Since it seems this might be a gvfs problem, testing KDE/konqueror seems like a logical step--I seem to recall that konqueror did not trigger the bug, bit it's been a while since I've tried.  Accessing the volume from the shell works normally, until one triggers the freeze, then nothing can access the volume until the gvfs process is killed (doing an 'ls' on the volume will just hang).  This makes me think something fishy may be going on in the kernel.

If anyone else has experienced this or has any ideas of how to diagnose this issue further, I would be most appreciative.

---

### Post by druhboruch on 2010-02-12
It is likely network problem.
It may be hardware problem.
I would try to change switch and cables first...

I run NFS4 with autofs on many computers and never ever had any problems with it.  It is like a rock.

---

### Post by computor on 2010-02-12
I doubt it's a hardware problem--this occurs at two different sites (different client/server pair, different switch, cables, etc).  It's good to know that it's working for some people, however.  What OS is your server? Ubuntu?

I'm wondering if this is an incompatibility w/opensolaris.  I know linux's NFS implementation has traditionally lagged behind Solaris' (Sun invented NFS, after all).

Are you doing any ID mapping/kerberos?  I'm doing id mapping, but no encryption.

---

### Post by tepsipakki on 2010-02-13
See for instance these threads on nfs4-list:

[http://linux-nfs.org/pipermail/nfsv4/2010-February/012069.html](http://linux-nfs.org/pipermail/nfsv4/2010-February/012069.html)
[http://linux-nfs.org/pipermail/nfsv4/2010-January/011860.html](http://linux-nfs.org/pipermail/nfsv4/2010-January/011860.html)

it's a real bug, and under discussion currently. I need to test if killing gvfs fixes it.

---

