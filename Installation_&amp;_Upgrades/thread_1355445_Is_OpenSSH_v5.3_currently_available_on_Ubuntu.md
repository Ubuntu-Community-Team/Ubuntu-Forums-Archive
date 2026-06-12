---
title: "Is OpenSSH v5.3 currently available on Ubuntu?"
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by watchpocket on 2009-12-14
I've started to delve into learning about SSH and would like to install the latest version, which openssh.com lists as "5.3/5.3p1", released on October 1st, 2009.

But the Synaptic Package Manager appears to have only version 5.1 available.

Is v5.3 not currently available for Ubuntu?  If not, I'll simply use 5.1.

If 5.3 is available, though, I'd prefer to use that.

---

### Post by watchpocket on 2009-12-14
Actually, I see that OpenSSH version 5.3 is available from distrowatch.com/ubuntuand other sites, but am curious as to why it isn't available in the Synaptic Package Manager?

---

### Post by earthpigg on 2009-12-15
> **watchpocket said:**
> Actually, I see that OpenSSH version 5.3 is available from distrowatch.com/ubuntuand other sites, but am curious as to why it isn't available in the Synaptic Package Manager?

each 6 month release of ubuntu comes with a certain predefined version of every program. for the entire support cycle of that ubuntu release, that release of that program is all that will be available.

security and other patches are applied, but otherwise that is the version you are stuck with if using official repositories.

userland graphical applications are sometimes backported, but basic things (like ssh) that folks rely on are frozen at the version that was current a month or two prior to the given ubuntu release. this is for the sake of stability and reliability.

if there are features of 5.3 that you need access to, then it may be worthwhile to compile it yourself... otherwise, sticking with the version that 'comes' with a given ubuntu release is kinda sorta the 'ubuntu' way of doing things. ubuntu's developers cannot test and verify that the most up-to-date version of every single of the 20,000 packages will work with every supported release of ubuntu, so they don't make them available by default.

if you want a rolling release distro (less reliability, less stability, but more latest-and-greatest software available via package manager), consider gentoo or arch or Debian Testing or Debian Unstable.

you will have 5.3 with the next ubuntu release, though :D

---

### Post by slakkie on 2009-12-20
Debian still has 5.1 in unstable, so I don't think Ubuntu will have it even in the current development release (which is based on Debian testing).

```

openssh-server:
  Installed: 1:5.1p1-8
  Candidate: 1:5.1p1-8
  Version table:
 *** 1:5.1p1-8 0
        800 ftp://ftp.nl.debian.org testing/main Packages
        990 ftp://ftp.nl.debian.org unstable/main Packages
        100 /var/lib/dpkg/status
     1:5.1p1-5 0
        500 ftp://ftp.nl.debian.org lenny/main Packages

openssh-server:
  Installed: 1:5.1p1-8ubuntu1
  Candidate: 1:5.1p1-8ubuntu1
  Version table:
 *** 1:5.1p1-8ubuntu1 0
        990 http://archive.ubuntu.com lucid/main Packages
        100 /var/lib/dpkg/status
     1:5.1p1-6ubuntu2 0
        900 http://archive.ubuntu.com karmic/main Packages

```

If you want to use openssh 5.3 you'll need to compile from source or update the current package..

---

