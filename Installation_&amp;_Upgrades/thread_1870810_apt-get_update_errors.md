---
title: "apt-get update errors"
date: 2011-10-27
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2011-10-27
Doing "apt-get update" is broken.  There was an issue with the /var filesystem, but fsck seemed to fix it.  But maybe not.  I get these error messages doing "apt-get update":

```
W: GPG error: http://security.ubuntu.com karmic-security Release: Couldn't access keyring: 'No such file or directory'
W: GPG error: http://us.archive.ubuntu.com karmic Release: Couldn't access keyring: 'No such file or directory'
W: GPG error: http://us.archive.ubuntu.com karmic-updates Release: Couldn't access keyring: 'No such file or directory'
```What file or directory is there no such?  How do I fix it?

---

### Post by drs305 on 2011-10-27
Those three repositories are for Karmic, which hasn't been supported since April. If you are running a newer version you should edit your sources.list to the release name you are using.

You can edit the sources.list with Ubuntu Tweak, manually via "gksu gedit /etc/apt/sources.list" or by opening Software Sources/Synaptic/Ubuntu Software Center.

---

### Post by fdrake on 2011-10-27
check also your release file
```

less /etc/lsb-release

```

---

### Post by Skaperen on 2011-10-31
> **drs305 said:**
> Those three repositories are for Karmic, which hasn't been supported since April. If you are running a newer version you should edit your sources.list to the release name you are using.

You can edit the sources.list with Ubuntu Tweak, manually via "gksu gedit /etc/apt/sources.list" or by opening Software Sources/Synaptic/Ubuntu Software Center.
1.  This really is Karmic :-(  So editing the sources list would be disasterous.

2.  I finally found someone on IRC that was able to help with the actual problem, which was that a gpg file was missing.  I was able to copy one from another machine.

3.  While Karmic SUPPORT is ended, the actual packages don't need to be disposed of.  They were in fact still there.  And if not there, they would be on the archive.

4.  Don't bother to suggest that I upgrade.  I'm in the process of setting up a replacement machine which will be installed with the latest LTS, and what's on this machine will be migrated to the new machine, gradually.  I needed to install tools on this machine to make the migration feasible.  Once the migration is complete, probably in January, this machine's drives will be shipped back to me and I will put something new on it (probably the same LTS).

---

