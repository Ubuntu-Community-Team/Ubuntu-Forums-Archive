---
title: "Fresh install broken already?"
date: 2014-08-30
forum: Installation &amp; Upgrades
---

### Post by Ian_Worrall on 2014-08-30
Hi all,

I have a baffling problem.
My fresh install of 14.04.1 desktop (used as a file server) with only Webmin, Sabnzbdplus, Transmission & ZFS-native installed is refusing to install any packages or updates.

It just returns:-
```

E: Waited for /usr/sbin/dpkg-preconfigure --apt || true but it wasn't there      
E: Failure running script /usr/sbin/dpkg-preconfigure --apt || true

```

I've read that this normally points to a malformed file at /etc/apt/apt.conf.d/70debconf, but that file reads correctly!

```

// Pre-configure all packages with debconf before they are installed.
// If you don't like it, comment it out.
DPkg::Pre-Install-Pkgs {"/usr/sbin/dpkg-preconfigure --apt || true";};

```

I've tried commenting the code out as stated above, but then get the following:-

```

dpkg: unrecoverable fatal error, aborting:
waiting for subprocess dpkg-split failed: No child processes
W: Waited for dpkg --assert-multi-arch but it wasn't there - dpkgGo (10: No child processes)
E: Couldn't wait for subprocess - waitpid (10: No child processes)
E:  Couldn't wait for subprocess - waitpid (10: No child processes)

```

Anyone have any ideas what to do next?

---

### Post by Ian_Worrall on 2014-08-30
Seems to be a Webmin error, as it doesn't show when accessed directly. Marking as solved.

---

### Post by dougsnell on 2015-02-04
Sorry for replying to a "solved" article, but you did such a good job scraping the issue, you're the #1 hit on Google.

I wouldn't call it a Webmin error, though.  The issue is you were trying to take a short-cut and use either the Command Shell or Text Login from Webmin modules.  If you go to the console and attempt what you were aiming for, it works just fine.  Probably a nice reason to add the ssh server module at this point.

Hope that helps someone.

---

### Post by Rocdufer on 2015-11-05
This was improperly marked as solved, because no warning message (W) or error message (E) got an explanation. The warning "W: Waited for dpkg --assert-multi-arch but it wasn't there - dpkgGo (10: No child processes)" means that the installer dpkg tried to use one of the foreign architectures (such as i386 over an amd64 system), however, the extra arch. was missing. One should add multi-arch support AND also add the missing architecture with the command « sudo dpkg --add-architecture  "arch." ». It follows that dpkg could not active a child process (10 message) and the system got tired of waiting for this "child" to run, that is the reported error « E: Couldn't wait for subprocess - waitpid (10: No child processes) ». After any warning or error message disappears, one could look for another guilty to blame, but it clearly looks that Webmin was innocent in this case.

Besides, it is unclear why to search for " /etc/apt/apt.conf.d/70debconf " . First, verify the presence of
" /usr/sbin/dpkg-preconfigure " because that was the first error message asked for.

That is, verify "debconf" package was properly installed.

---

