---
title: "Can't update anything."
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by marcjboudreau on 2007-04-25
So, no matter what I do I can't seem to fix this. Right now I can't update my sources, when I try I get this error

```
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
```

Then this one

```

E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-universe.list (dist parse)
E: Unable to lock the list directory
```

when I type

```
sudo gedit /etc/apt/sources.list
```

I get

```

# Automatically generated sources.lisl
# http://www.ubuntu-nl.org/source-o-matic/
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# https://help.ubuntu.com/community/Repositories/CommandLine

# Ubuntu supported packages
# GPG key: 437D05B5
deb http://ca.archive.ubuntu.com/ubuntu/ edgy main restricted
deb http://ca.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb http://security.ubuntu.com/ubuntu edgy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://ca.archive.ubuntu.com/ubuntu/ edgy universe multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ edgy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu edgy-security universe multiverse

# Seveas' Ubuntu Packages
# GPG key: 1135D466
deb http://mirror.ubuntulinux.nl/ edgy-seveas all

# Medibuntu multimedia packages
# GPG key: 0C5A2783
deb http://medibuntu.sos-sts.com/repo/ edgy free non-free

# Canonical Commercial packages
# GPG key: 437D05B5
deb http://archive.canonical.com edgy-commercial main
```

I've tried just about everything I can think of. Any ideas of how to fix this?

posted here as well, [http://ubuntuforums.org/showthread.php?t=421992](http://ubuntuforums.org/showthread.php?t=421992), but I think it was the wrong forum for it. Sorry if I shouldn't post multiples.

---

