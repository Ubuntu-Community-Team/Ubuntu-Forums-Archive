---
title: "[SOLVED] Repositories won't function after upgrade"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by rhankins on 2007-10-22
After upgrading from 7.04 to 7.10, I have lost the ability to access some repositories.  I received an error **after** I followed the steps at Psychocats.  I will have to say, it's better than it was before I followed the instructions, but here's the error I receive in Synaptic Package Manager:

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://archive.canonical.com/ubuntu/dists/gutsy-commercial/main/binary-i386/Packages.gz:](http://archive.canonical.com/ubuntu/dists/gutsy-commercial/main/binary-i386/Packages.gz:) 404 Not Found
[http://medibuntu.sos-sts.com/repo/dists/gutsy/free/binary-i386/Packages.gz:](http://medibuntu.sos-sts.com/repo/dists/gutsy/free/binary-i386/Packages.gz:) 302 Found
[http://medibuntu.sos-sts.com/repo/dists/gutsy/non-free/binary-i386/Packages.gz:](http://medibuntu.sos-sts.com/repo/dists/gutsy/non-free/binary-i386/Packages.gz:) 302 Found
[http://medibuntu.sos-sts.com/repo/dists/gutsy/free/source/Sources.gz:](http://medibuntu.sos-sts.com/repo/dists/gutsy/free/source/Sources.gz:) 302 Found
[http://medibuntu.sos-sts.com/repo/dists/gutsy/non-free/source/Sources.gz:](http://medibuntu.sos-sts.com/repo/dists/gutsy/non-free/source/Sources.gz:) 302 Found

Thanks in advance for any suggestions/solutions

---

### Post by seldenthuis on 2007-10-22
Gutsy no longer uses the commercial repository, but the 'partner' one and medibuntu moved to packages.medibuntu.org.  Replace the bad lines in  /etc/apt/sources.list with

```

deb http://archive.canonical.com/ubuntu gutsy partner
deb http://packages.medibuntu.org/ gutsy free non-free

```

---

### Post by rhankins on 2007-10-22
Worked beautifully!  Thanks!!! :)

---

