---
title: "&quot;Permission denied&quot; when upgrading Feisty to Gutsy server with do-release-upgrade"
date: 2007-11-17
forum: Installation &amp; Upgrades
---

### Post by wammin on 2007-11-17
I was just handed a Ubuntu server on a hosted VPS in order to set up a web hosting environment. The first thing I found out was that the server was installed with 7.04. I want 7.10, specifically for the updated Nginx package. Anyway ... before I did anything else, I tried to upgrade and got this wierd permission error. Any ideas?

```
# do-release-upgrade
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading            
extracting '/tmp/tmpnNHX20/gutsy.tar.gz'
authenticate '/tmp/tmpnNHX20/gutsy.tar.gz' against '/tmp/tmpnNHX20/gutsy.tar.gz.gpg' 
Traceback (most recent call last):
  File "/usr/bin/do-release-upgrade", line 45, in <module>
    fetcher.run()
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 178, in run
    self.runDistUpgrader()
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 143, in runDistUpgrader
    os.execv(self.script,[self.script]+self.run_options)
OSError: [Errno 13] Permission denied
```

I tried running as root and also as a regular user with sudo ... same issue. What file is actually having permission problems?

---

### Post by Oldster on 2007-11-17
Are you running the command as root?

Maybe try:

sudo do-release-upgrade

then enter the root password.

---

### Post by wammin on 2007-11-17
> **wammin said:**
> I tried running as root and also as a regular user with sudo ... same issue. What file is actually having permission problems?

Yes. As I said, I tried the upgrade as root and also using sudo.

---

### Post by mershcel on 2007-12-17
I encountered this problem because the server's /tmp partition was mounted as noexec (so that you can't run programs or scripts in the /tmp folder).

A good idea from a security perspective (it prevents a surprising number of exploits). 

Because the installer downloads an updated copy of itself, verifies the signature, and runs that from the /tmp folder, it fails if your /tmp is noexec.

Solution: Change the mount settings in /etc/fstab to remove noexec for /tmp, umount /tmp, mount /tmp.

Might be a good idea to change it back afterwards, as it's a useful hardening, especially for web hosts.

---

