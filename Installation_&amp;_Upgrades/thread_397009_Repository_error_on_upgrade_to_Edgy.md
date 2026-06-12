---
title: "Repository error on upgrade to Edgy"
date: 2007-03-30
forum: Installation &amp; Upgrades
---

### Post by peterwr on 2007-03-30
Hi All

Sorry if this has been covered elsewhere - I've done a forum search and read the stickies, but nothing quite seems to cover it. Here goes:

I've recently upgraded from Dapper to Edgy. My system has both Gnome and KDE enabled, so the repository list is quite long. A colleague told me to upgrade by changing every instance of "dapper" in /etc/apt/sources.lit to "edgy" (I know, I know, RTFM...:(  ). Not surprisingly, with hindsight, I now get an error - a slew of errors, more like - when I try to refresh the package list, update software, etc. I've looked at the lists of repositories in the sticky posts, but they seem to be specific to standard installs of G, K or X. So, here's the list of errors I've been getting and I'm hoping somebody can point out the error(s) of my ways. Pretty please? 

When I Reload the list, Synaptic gets to file 68 of 74 and hangs. if I hit the Cancel button I get:

> Could not download all repository indexes

"The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

And this list of errors:

> http://packages.freecontrib.org/plf/dists/edgy-plf/Release.gpg
http://packages.freecontrib.org/plf/dists/edgy-plf/free/i18n/Translation-en_GB.bz2
http://packages.freecontrib.org/plf/dists/edgy-plf/non-free/i18n/Translation-en_GB.bz2
http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2: Sub-process bzip2 returned an error code (2)
http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2: Sub-process bzip2 returned an error code (2)

- any ideas? 

TIA,


Peter

---

### Post by zvacet on 2007-03-31
These are PLF repositories and they are replaced by medibuntu.
[http://easylinux.info/wiki/Ubuntu_Edgy#How_to_add_extra_repositories]("http://easylinux.info/wiki/Ubuntu_Edgy#How_to_add_extra_repositories")

Remove PLF and add medibuntu.After that 

```
sudo aptitude update
```

---

