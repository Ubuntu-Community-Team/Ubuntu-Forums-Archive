---
title: "is this debian etch repository safe for feisty?"
date: 2007-07-02
forum: Installation &amp; Upgrades
---

### Post by fflarex on 2007-07-02
I really want some of the things included in there, and finally found some .deb files for them, but I'm not sure how to get at them without adding the repository. How much difference does it really make whether you have a repository for one distro/version vs. another? I thought .deb files were fairly interchangeable with other distros, but then why are some third-party repositories made only for specific distros?

[http://www.rarewares.org/debian-info-apt.php](http://www.rarewares.org/debian-info-apt.php)

---

### Post by rillip on 2007-07-03
Adding that as a repo is a very bad idea.  It Debian has a lot older kernels, older program versions, older pretty much everything.  That's just the way Debian works, the release cyhcle is a lot slower.  You're inviting a lot of incompatibility problems by adding it because of the version mismatches.  Installing a deb is reasonably safe because it only installs the one program and doesn't resolve dependancies.

---

### Post by fflarex on 2007-07-03
So is there a way to get just one or two files out of it without adding it as a source? I want some of the audio encoders it has in it, which I haven't been able to find any information on whatsoever concerning how to install them. Searches and forum posts have turned up nothing. It seems most technically-oriented, nit-picky audiophiles such as myself use Windows.

---

