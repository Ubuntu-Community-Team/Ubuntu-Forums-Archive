---
title: "apt-get autoremove deletes libreoffice writer!"
date: 2014-09-18
forum: Installation &amp; Upgrades
---

### Post by Tze_Veh on 2014-09-18
Hi all,

Since a couple months I'm getting this output after installing new system updates:

```
The following packages were automatically installed and are no longer required:
  hyphen-en-us libreoffice-help-en-gb libreoffice-help-en-us
  libreoffice-l10n-en-gb libreoffice-l10n-en-za libreoffice-math
  libreoffice-writer mythes-en-au mythes-en-us openoffice.org-hyphenation
  python-rsvg python-webkit
Use 'apt-get autoremove' to remove them.

```

The first time I thought it was some previous version and just went on, but had to realize it's actually deleting my go-to document editor, no questions asked. Had to reinstall, and now I'm looking for a way to prevent this (but I still want to use the autoremove feature).

Any ideas?

---

### Post by vasa1 on 2014-09-18
Can you please post the output between code tags of the two text files created by running
```
dpkg --get-selections | grep "libreoffice" > ~/Desktop/libre.txt
```and```
dpkg --get-selections | grep "openoffice" > ~/Desktop/open.txt
```

---

### Post by ian-weisser on 2014-09-18
Packages are eligible for autoremoval when BOTH of the following conditions occur:

1) The package was not explicitly installed by the user. Instead, the package was installed as a dependency of something else. 
apt calls this 'auto'-installed instead of 'manual'-installed.

2) It's an orphan. 'Something else' is no longer installed.

So the system thought, before your reinstall, you didn't want Write.
Since you really did explicitly want libreoffice-writer, you could simply tell the system so, changing #1 above.
```
sudo apt-get install libreoffice-writer
```

The command won't download and reinstall Write. Instead, it will simply change that apt-mark.

A more advanced command that does exactly the same thing:
```
sudo apt-mark manual libreoffice-writer
```

---

