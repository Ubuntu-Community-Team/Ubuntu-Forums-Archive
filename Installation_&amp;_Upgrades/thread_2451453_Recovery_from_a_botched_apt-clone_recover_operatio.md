---
title: "Recovery from a botched apt-clone recover operation?"
date: 2020-10-04
forum: Installation &amp; Upgrades
---

### Post by poltr1 on 2020-10-04
I'm upgrading from a Dell Latitude D630 laptop running bionic to a Dell Latitude E6530 laptop running focal.  I ran "apt-clone clone (output-file)" on the old laptop to create a list of installed packages.  Problem is, it also copied the version number into the output file, along with the package name.  So when I ran "apt-clone restore (output-file)" on the new laptop, it tried to get the packages from bionic and not focal.  (D'oh!). 

The question is: Is there a graceful way to recover from this situation?  Or should I just reinstall focal on the new system?

Also, is there a parameter or qualifier for apt-clone to copy package names only?  If not, I'll just use dpkg and pipe the output through awk to extract the package names.

---

### Post by ynota on 2020-10-05
I can't speak from experience but looking at the Man [page]("http://manpages.ubuntu.com/manpages/bionic/man8/apt-clone.8.html") maybe you should have used "apt-clone [COLOR=#111111][FONT=monospace]restore-new-distro"[/FONT][/COLOR]

---

### Post by poltr1 on 2020-10-07
Yeah.  The page I found on 2daygeek.com didn't mention the restore-new-distro parameter.  That's what I get for not RTFM'ing.  :-( 

Ah well.  I'll reimage.  At least I didn't lose any data.

---

