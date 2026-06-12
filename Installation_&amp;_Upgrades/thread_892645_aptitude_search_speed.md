---
title: "aptitude search speed"
date: 2008-08-17
forum: Installation &amp; Upgrades
---

### Post by oconnor663 on 2008-08-17
Are there any utilities for APT that speed up package searching? I'm familiar only with Gentoo esearch, which is instantaneous and includes helpful version/status information. I've heard apt-cache mentioned, but is there any way to have that give a more informative output? Thanks much.

---

### Post by drboontu on 2008-08-17
Hi,

# apt-cache search <package>
# apt-cache show <package>

# dpkg -l | grep  <package>

e.g.
# apt-cache search gedit
# apt-cache show gedit

# dpkg -l | grep gedit

$ dpkg --get-selections > software

This will create the file "software" in your home directory, showing all installed packages.

Cheers,

---

