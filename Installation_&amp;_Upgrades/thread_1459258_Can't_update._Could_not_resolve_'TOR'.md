---
title: "Can't update. Could not resolve 'TOR'"
date: 2010-04-21
forum: Installation &amp; Upgrades
---

### Post by Dark_Wrath on 2010-04-21
I'm running Ubuntu 9.10 along with Windows 7. I tried installing the TOR proxy thing long back, and today when I tried downloading a package it gave me that. Now even if I try updating my system, it says:-

[IMG]http://bayimg.com/image/aamiiaaca.jpg[/IMG]

```

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg  Could not resolve 'TOR'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_IN.bz2  Could not resolve 'TOR'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_IN.bz2  Could not resolve 'TOR'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_IN.bz2  Could not resolve 'TOR'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_IN.bz2  Could not resolve 'TOR'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg  Could not resolve 'TOR'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_IN.bz2  Could not resolve 'TOR'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_IN.bz2  Could not resolve 'TOR'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_IN.bz2  Could not resolve 'TOR'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_IN.bz2  Could not resolve 'TOR'

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/karmic/Release.gpg  Could not resolve 'TOR'

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/karmic/partner/i18n/Translation-en_IN.bz2  Could not resolve 'TOR'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg  Could not resolve 'TOR'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_IN.bz2  Could not resolve 'TOR'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_IN.bz2  Could not resolve 'TOR'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_IN.bz2  Could not resolve 'TOR'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_IN.bz2  Could not resolve 'TOR'

W: Failed to fetch http://dl.google.com/linux/deb/dists/stable/Release.gpg  Could not resolve 'TOR'

W: Failed to fetch http://dl.google.com/linux/deb/dists/stable/main/i18n/Translation-en_IN.bz2  Could not resolve 'TOR'

W: Failed to fetch http://packages.medibuntu.org/dists/karmic/Release.gpg  Could not resolve 'TOR'

W: Failed to fetch http://packages.medibuntu.org/dists/karmic/free/i18n/Translation-en_IN.bz2  Could not resolve 'TOR'

W: Failed to fetch http://packages.medibuntu.org/dists/karmic/non-free/i18n/Translation-en_IN.bz2  Could not resolve 'TOR'

W: Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

I can't update OR even downlaod a single package using the Synaptic Manager or the Terminal. I can still download using debian files I get from online, but not everything works that way.

---

### Post by Dark_Wrath on 2010-04-21
Bump! Is there a solution to this except for me having tor reinstall Ubuntu?

---

### Post by andrewthomas on 2010-04-21
Look in synaptic under Settings > Preferences > Network and make sure that you have direct connection to the internet  selected and not manual proxy configuration.

---

