---
title: "Upgrade to 13.10 fails during do-release-upgrade"
date: 2013-10-24
forum: Installation &amp; Upgrades
---

### Post by jcoxen on 2013-10-24
I'm trying to upgrade from 13.04 to 13.10 but do-release-upgrade fails with the following:

```
~$ do-release-upgrade
Checking for a new Ubuntu release
WARNING:root:could not open file '/etc/apt/sources.list'

WARNING:root:could not open file '/etc/apt/sources.list'

Get:1 Upgrade tool signature [198 B]
Get:2 Upgrade tool [1,136 kB]
Fetched 1,136 kB in 0s (0 B/s)
authenticate 'saucy.tar.gz' against 'saucy.tar.gz.gpg'
extracting 'saucy.tar.gz'

Reading cache


A fatal error occurred

Please report this as a bug and include the files
/var/log/dist-upgrade/main.log and /var/log/dist-upgrade/apt.log in
your report. The upgrade has aborted.
Your original sources.list was saved in
/etc/apt/sources.list.distUpgrade.

Traceback (most recent call last):

File "/tmp/ubuntu-release-upgrader-0h8qe4/saucy", line 10, in
<module>
sys.exit(main())

File
"/tmp/ubuntu-release-upgrader-0h8qe4/DistUpgrade/DistUpgradeMain.py",
line 240, in main
save_system_state(logdir)

File
"/tmp/ubuntu-release-upgrader-0h8qe4/DistUpgrade/DistUpgradeMain.py",
line 133, in save_system_state
scrub_sources=True)

File "/tmp/ubuntu-release-upgrader-0h8qe4/DistUpgrade/apt_clone.py",
line 149, in save_state
self._write_state_sources_list(tar, scrub_sources)

File "/tmp/ubuntu-release-upgrader-0h8qe4/DistUpgrade/apt_clone.py",
line 230, in _write_state_sources_list
"./etc/apt/sources.list")

File "/tmp/ubuntu-release-upgrader-0h8qe4/DistUpgrade/apt_clone.py",
line 246, in _add_file_to_tar_with_password_check
for line in f.readlines():

File "/usr/lib/python2.7/codecs.py", line 296, in decode
(result, consumed) = self._buffer_decode(data, self.errors, final)

UnicodeDecodeError: 'utf8' codec can't decode byte 0xd0 in position
2818: invalid continuation byte


```

Any suggestions for correcting this?

---

### Post by Dennis N on 2013-10-24
You need to use sudo:

**sudo do-release-upgrade**

---

### Post by jcoxen on 2013-10-24
Using sudo doesn't affect this problem.  If I don't start with sudo it prompts me for my password.  If I do start with sudo it still dies in exactly the same manner.  The only reason you don't see the password prompt my original post is because I ran it a second time to copy the output for the post so my password was cached.

---

