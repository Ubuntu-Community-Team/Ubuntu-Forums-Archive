---
title: "Apt/dpkg error from manually-deleted packages"
date: 2007-07-07
forum: Installation &amp; Upgrades
---

### Post by TheForkOfJustice on 2007-07-07
I tried to delete some packages by deleting them manually but it created an error in apt.

I now get this output whenever I try to uninstall something:

```

dpkg: serious warning: files list file for package `texlive-base' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `texlive-doc-base' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `texlive-fonts-recommended' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `texlive-base-bin' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `texlive-latex-recommended' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `texlive-latex-base' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `texlive-common' missing, assuming package has no files currently installed.

```

How do I get rid of the error?

---

### Post by bmorency on 2007-07-07
what happens when you try to reinstall those packages?

---

### Post by TheForkOfJustice on 2007-07-07
> **bmorency said:**
> what happens when you try to reinstall those packages?

I got an error saying the packages were already installed when I tried to reinstall using apt-get.

I managed to solve my problem by using aptitude.  It allowed me to fully remove the remnants of the packages.

Problem solved.

---

