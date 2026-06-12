---
title: "Terminal errors, what they mean? How can I solve? (Ubuntu 20.04)"
date: 2022-01-30
forum: Installation &amp; Upgrades
---

### Post by renanrischiotto1 on 2022-01-30
```
renan@ubuntupc:~$ sudo apt update
[sudo] password for renan: 
Hit:1 http://br.archive.ubuntu.com/ubuntu focal InRelease
Get:2 http://br.archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]  
Get:3 http://br.archive.ubuntu.com/ubuntu focal-backports InRelease [108 kB]   
Hit:4 https://dl.google.com/linux/chrome/deb stable InRelease                  
Ign:5 http://br.archive.ubuntu.com/ubuntu focal-updates/main amd64 DEP-11 Metadata
Ign:6 http://br.archive.ubuntu.com/ubuntu focal-updates/universe amd64 DEP-11 Metadata
Ign:7 http://br.archive.ubuntu.com/ubuntu focal-updates/multiverse amd64 DEP-11 Metadata
Get:5 http://br.archive.ubuntu.com/ubuntu focal-updates/main amd64 DEP-11 Metadata [281 kB]
Err:5 http://br.archive.ubuntu.com/ubuntu focal-updates/main amd64 DEP-11 Metadata
  File has unexpected size (281900 != 281380). Mirror sync in progress? [IP: 2801:82:80ff:8000::5 80]
  Hashes of expected file:
   - Filesize:281380 [weak]
   - SHA256:e17e1dd8811301e6df7ea63bd18cd30b821cf1b0acefd4f43643c33a667dfaf4
   - SHA1:f792fd2e8531117e4edeb921c2d7e443cf1e27fc [weak]
   - MD5Sum:65e10c25f991006cb743a97d623e5eb0 [weak]
  Release file created at: Sun, 30 Jan 2022 19:23:49 +0000
Get:6 http://br.archive.ubuntu.com/ubuntu focal-updates/universe amd64 DEP-11 Metadata [364 kB]
Err:6 http://br.archive.ubuntu.com/ubuntu focal-updates/universe amd64 DEP-11 Metadata
  
Get:7 http://br.archive.ubuntu.com/ubuntu focal-updates/multiverse amd64 DEP-11 Metadata [944 B]
Get:7 http://br.archive.ubuntu.com/ubuntu focal-updates/multiverse amd64 DEP-11 Metadata [944 B]
Get:7 http://br.archive.ubuntu.com/ubuntu focal-updates/multiverse amd64 DEP-11 Metadata [944 B]
Get:7 http://br.archive.ubuntu.com/ubuntu focal-updates/multiverse amd64 DEP-11 Metadata [944 B]
Err:7 http://br.archive.ubuntu.com/ubuntu focal-updates/multiverse amd64 DEP-11 Metadata
  
Ign:11 http://br.archive.ubuntu.com/ubuntu focal-backports/main amd64 DEP-11 Metadata
Ign:12 http://br.archive.ubuntu.com/ubuntu focal-backports/universe amd64 DEP-11 Metadata
Get:11 http://br.archive.ubuntu.com/ubuntu focal-backports/main amd64 DEP-11 Metadata [7.996 B]
Err:11 http://br.archive.ubuntu.com/ubuntu focal-backports/main amd64 DEP-11 Metadata
  File has unexpected size (7972 != 7996). Mirror sync in progress? [IP: 2801:82:80ff:8000::5 80]
  Hashes of expected file:
   - Filesize:7996 [weak]
   - SHA256:a7e3c8ac2ae338ec865929a3c7e78fb93a2602d87d81b542094f14124b8d9a0e
   - SHA1:e980132e11c446c812eff0edeaf77bf11c87ec4a [weak]
   - MD5Sum:494b9557774e4a622c7138d0036fdaf3 [weak]
  Release file created at: Sun, 30 Jan 2022 18:56:48 +0000
Hit:13 http://security.ubuntu.com/ubuntu focal-security InRelease              
Get:12 http://br.archive.ubuntu.com/ubuntu focal-backports/universe amd64 DEP-11 Metadata [12,0 kB]
Err:12 http://br.archive.ubuntu.com/ubuntu focal-backports/universe amd64 DEP-11 Metadata
  
Hit:14 http://archive.canonical.com/ubuntu focal InRelease   
Fetched 223 kB in 1s (274 kB/s)
Reading package lists... Done
E: Failed to fetch http://br.archive.ubuntu.com/ubuntu/dists/focal-updates/main/dep11/Components-amd64.yml.xz  File has unexpected size (281900 != 281380). Mirror sync in progress? [IP: 2801:82:80ff:8000::5 80]
   Hashes of expected file:
    - Filesize:281380 [weak]
    - SHA256:e17e1dd8811301e6df7ea63bd18cd30b821cf1b0acefd4f43643c33a667dfaf4
    - SHA1:f792fd2e8531117e4edeb921c2d7e443cf1e27fc [weak]
    - MD5Sum:65e10c25f991006cb743a97d623e5eb0 [weak]
   Release file created at: Sun, 30 Jan 2022 19:23:49 +0000
E: Failed to fetch http://br.archive.ubuntu.com/ubuntu/dists/focal-updates/universe/dep11/Components-amd64.yml.xz  
E: Failed to fetch http://br.archive.ubuntu.com/ubuntu/dists/focal-updates/multiverse/dep11/Components-amd64.yml.xz  
E: Failed to fetch http://br.archive.ubuntu.com/ubuntu/dists/focal-backports/main/dep11/Components-amd64.yml.xz  File has unexpected size (7972 != 7996). Mirror sync in progress? [IP: 2801:82:80ff:8000::5 80]
   Hashes of expected file:
    - Filesize:7996 [weak]
    - SHA256:a7e3c8ac2ae338ec865929a3c7e78fb93a2602d87d81b542094f14124b8d9a0e
    - SHA1:e980132e11c446c812eff0edeaf77bf11c87ec4a [weak]
    - MD5Sum:494b9557774e4a622c7138d0036fdaf3 [weak]
   Release file created at: Sun, 30 Jan 2022 18:56:48 +0000
E: Failed to fetch http://br.archive.ubuntu.com/ubuntu/dists/focal-backports/universe/dep11/Components-amd64.yml.xz  
E: Some index files failed to download. They have been ignored, or old ones used instead.
renan@ubuntupc:~$

```

---

### Post by deadflowr on 2022-01-30
> Mirror sync in progress? 
Try to wait it out and see if that was the issue.

---

### Post by renanrischiotto1 on 2022-01-30
Thanks for the attention. Well how long should I wait?

---

### Post by deadflowr on 2022-01-30
If it (mirror syncing) is the problem it will be resolved in a few minutes, usually.
If it's not then there is probably a bigger issue at hand.

Most of the time this is a mirror sync issue.

I won't say it's definitely the issue,
but it's fair to say it's normally the issue.

---

### Post by renanrischiotto1 on 2022-01-30
Looks like it's all normal now, thanks!

---

