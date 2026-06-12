---
title: "update errors"
date: 2012-08-19
forum: Installation &amp; Upgrades
---

### Post by MakOwner on 2012-08-19
I'm getting this from desktop updates over the last few hours:

```

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_universe_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

```

Any ideas?
Where should I "please report" this?

---

### Post by tommcd on 2012-08-19
It seems that this is a known bug that has been reported to Launchpad. See these pages for the fix:
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1010212](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1010212)
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/346386](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/346386)
[http://ubuntuforums.org/showthread.php?t=1981184](http://ubuntuforums.org/showthread.php?t=1981184)
[http://ubuntuforums.org/showthread.php?t=1978554](http://ubuntuforums.org/showthread.php?t=1978554)
I found these very quickly by googleing the error you posted.

---

### Post by MakOwner on 2012-09-13
> **tommcd said:**
> It seems that this is a known bug that has been reported to Launchpad. See these pages for the fix:
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1010212](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1010212)
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/346386](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/346386)
[http://ubuntuforums.org/showthread.php?t=1981184](http://ubuntuforums.org/showthread.php?t=1981184)
[http://ubuntuforums.org/showthread.php?t=1978554](http://ubuntuforums.org/showthread.php?t=1978554)
I found these very quickly by googleing the error you posted.

After several attempts at those solutions, I now get this:
```

W: GPG error: http://archive.canonical.com precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://archive.ubuntu.com precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

```



This [http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html](http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html) appears to be the suggested fix, but does not remove the error, although command line updates will work after doing this.

---

