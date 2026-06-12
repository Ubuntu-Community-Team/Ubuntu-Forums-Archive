---
title: "Package updates not authenticating, &quot;BADSIG&quot;"
date: 2010-03-08
forum: Installation &amp; Upgrades
---

### Post by andrewjensen90 on 2010-03-08
I'm running into strange authentication problems when I install or update packages on my machine (Karmic 9.10).  When I run the update manager, it downloads 34 files and then gives me an error dialog:

```
W: GPG error: http://archive.canonical.com karmic Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://security.ubuntu.com karmic-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://us.archive.ubuntu.com karmic Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://us.archive.ubuntu.com karmic-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/Release  

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

So apparently my computer wants to install packages using a signature "BADSIG 409..."?  What's wrong?  I apparently haven't been able to install updates in the last 38 days, which concerns me...

---

### Post by andrewjensen90 on 2010-03-24
Found a solution here:

[http://en.newinstance.it/2009/06/22/the-following-signatures-were-invalid-badsig-40976eaf437d05b5-ubuntu-archive-automatic-signing-key/](http://en.newinstance.it/2009/06/22/the-following-signatures-were-invalid-badsig-40976eaf437d05b5-ubuntu-archive-automatic-signing-key/)

```
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update
```

---

