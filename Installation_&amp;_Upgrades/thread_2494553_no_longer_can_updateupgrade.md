---
title: "no longer can update/upgrade"
date: 2024-01-20
forum: Installation &amp; Upgrades
---

### Post by dchmelik on 2024-01-20
We have a few Ubuntu 22.04.3 variant PCs which one stopped updating/upgrading, so now runs an older kernel than the others, and other outdated software, the only major difference which is this PC has less stuff installed on it (you'd think might lead to fewer problems).  For some days/weeks when updating it always says something like the below, even if I 'apt clean' and 'apt --fix-broken install'.  Is this going to require a fresh reinstallation?  The PCs are configured the same and on the same local area network (LAN) the others don't have problems updating/upgrading.

```

[FONT=monospace][COLOR=#000000]root@office:~# [/COLOR][/FONT]apt-get update && apt-get dist-upgrade
[...]
[FONT=monospace][COLOR=#000000]Err:18 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 c-n-f Metadata                                                                   [/COLOR]
                                              
  Hash Sum mismatch
  Hashes of expected file:
   - Filesize:64514 [weak]
   - SHA256:9ad2ca1e8851596cc020b4bf77ef22791c3f60a3541b930451144edd4b7bb86f
   - SHA1:73ae0d8b23f73ddb48efcc727062ba3d6ccc2b2a [weak]
   - MD5Sum:06e29fa4794d9e573608b29e1e84f0f4 [weak]
  Hashes of received file:
   - SHA256:e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855
   - SHA1:da39a3ee5e6b4b0d3255bfef95601890afd80709 [weak]
   - MD5Sum:d41d8cd98f00b204e9800998ecf8427e [weak]
   - Filesize:0 [weak]
  Release file created at: Sat, 20 Jan 2024 03:49:17 +0000
Fetched 152 MB in 2min 10s (1,172 kB/s)
Reading package lists... Done
E: Failed to fetch store:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_jammy-updates_main_cnf_Commands-amd64  Hash Sum mismatch
   Hashes of expected file:
    - Filesize:64514 [weak]
    - SHA256:9ad2ca1e8851596cc020b4bf77ef22791c3f60a3541b930451144edd4b7bb86f
    - SHA1:73ae0d8b23f73ddb48efcc727062ba3d6ccc2b2a [weak]
    - MD5Sum:06e29fa4794d9e573608b29e1e84f0f4 [weak]
   Hashes of received file:
    - SHA256:e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855
    - SHA1:da39a3ee5e6b4b0d3255bfef95601890afd80709 [weak]
    - MD5Sum:d41d8cd98f00b204e9800998ecf8427e [weak]
    - Filesize:0 [weak]
   Release file created at: Sat, 20 Jan 2024 03:49:17 +0000
E: Some index files failed to download. They have been ignored, or old ones used instead.
[/FONT]
```

---

### Post by TheFu on 2024-01-20
If you've wasted more than 1 hour on this problem, it is too much. Just wipe the system and restore from the backup just before the issues started then patch.  If the issue returns, look for storage corruption problems (fsck/smartctl) and be 100% certain the patch process has been updating the local package caches.

BTW, best to show the exact, full, command, being used.  There are 2 commands required to update Ubuntu.

---

### Post by deadflowr on 2024-01-20
Typically you could try
```
sudo rm -rf /var/lib/apt/lists/*
sudo apt update
```

Double check that there are no spaces in the /var/lib/apt/lists directory path.
You could also cd in the lists directory just to be safer
```
cd /var/lib/apt/lists
sudo rm *
```

If that doesn't help post the output of the apt update command.

---

### Post by dchmelik on 2024-01-21
I don't spend much time watching upgrades and it'd take a lot for me to reinstall.  The second reply's instructions solved this; thanks!

---

### Post by TheFu on 2024-01-21
> **dchmelik said:**
> I don't spend much time watching upgrades and it'd take a lot for me to reinstall.  The second reply's instructions solved this; thanks!

Glad you found a solution, but if restoring from a backup takes more than 1 hour, you are doing backups wrong and you need a better method.

---

