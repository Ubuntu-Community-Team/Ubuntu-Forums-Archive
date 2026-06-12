---
title: "Corrupted file in mirror http://br.archive.ubuntu.com"
date: 2021-07-17
forum: Installation &amp; Upgrades
---

### Post by ricleite on 2021-07-17
Hi!
Where would be the correct location for me to report this problem and potential security breach?


```

 root@ric-Inspiron-5558:~# apt-get updateHit:1 [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) focal InRelease
Get:2 [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) bionic InRelease [64.4 kB]       
Get:3 [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) focal-updates InRelease [114 kB]                                    
Hit:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease
Get:5 [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) focal-backports InRelease [101 kB]
Ign:6 [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) focal-updates/main amd64 DEP-11 Metadata
Ign:7 [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) focal-updates/universe amd64 DEP-11 Metadata
Ign:8 [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) focal-updates/multiverse amd64 DEP-11 Metadata
Get:6 [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) focal-updates/main amd64 DEP-11 Metadata [283 kB]
Err:6 [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) focal-updates/main amd64 DEP-11 Metadata
  File has unexpected size (282428 != 282524). Mirror sync in progress? [IP: 2801:82:80ff:8000::5 80]
  Hashes of expected file:
   - Filesize:282524 [weak]
   - SHA256:1c161c4f2e5e70a0fe798fd88ae1e1db4b1f87547d10d7b7ff12d4ea33653701
   - SHA1:29755f08fced4eea9b0a96ab44c04a3d358fddd5 [weak]
   - MD5Sum:ee219c3d3bdaec38b97bd5fa39aacec7 [weak]
  Release file created at: Sat, 17 Jul 2021 11:20:08 +0000
Ign:9 [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) focal-backports/universe amd64 DEP-11 Metadata
Get:7 [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) focal-updates/universe amd64 DEP-11 Metadata [334 kB]
Err:7 [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) focal-updates/universe amd64 DEP-11 Metadata
  
Get:8 [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) focal-updates/multiverse amd64 DEP-11 Metadata [2,468 B]
Err:8 [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) focal-updates/multiverse amd64 DEP-11 Metadata
  
Get:9 [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) focal-backports/universe amd64 DEP-11 Metadata [10.3 kB]
Err:9 [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) focal-backports/universe amd64 DEP-11 Metadata
  Hash Sum mismatch
  Hashes of expected file:
   - Filesize:10328 [weak]
   - SHA256:3566fd2912a25cd3d01b230acbaa51e61b4e99f1b984fdd1eac52125c4daea68
   - SHA1:6e704c7a3840db937c83681785a9a716898897e3 [weak]
   - MD5Sum:74d117d81a79fa52fdf1a1a1449582b8 [weak]
  Hashes of received file:
   - SHA256:b00a4fd108011f79a78816ef00f7070dccb21465f8fd61fcc88e56d86315ab1c
   - SHA1:dd4b3f85ec6159216b133c9426c8010bf98caa47 [weak]
   - MD5Sum:cac480dddf202b846c2b322587c99447 [weak]
   - Filesize:10328 [weak]
  Last modification reported: Sat, 17 Jul 2021 07:22:09 +0000
  Release file created at: Sat, 17 Jul 2021 11:20:47 +0000
Fetched 292 kB in 1s (257 kB/s)              
Reading package lists... Done
E: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/focal-updates/main/dep11/Components-amd64.yml.xz](http://br.archive.ubuntu.com/ubuntu/dists/focal-updates/main/dep11/Components-amd64.yml.xz)  File has unexpected size (282428 != 282524). Mirror sync in progress? [IP: 2801:82:80ff:8000::5 80]
   Hashes of expected file:
    - Filesize:282524 [weak]
    - SHA256:1c161c4f2e5e70a0fe798fd88ae1e1db4b1f87547d10d7b7ff12d4ea33653701
    - SHA1:29755f08fced4eea9b0a96ab44c04a3d358fddd5 [weak]
    - MD5Sum:ee219c3d3bdaec38b97bd5fa39aacec7 [weak]
   Release file created at: Sat, 17 Jul 2021 11:20:08 +0000
E: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/focal-updates/universe/dep11/Components-amd64.yml.xz](http://br.archive.ubuntu.com/ubuntu/dists/focal-updates/universe/dep11/Components-amd64.yml.xz)  
E: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/focal-updates/multiverse/dep11/Components-amd64.yml.xz](http://br.archive.ubuntu.com/ubuntu/dists/focal-updates/multiverse/dep11/Components-amd64.yml.xz)  
E: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/focal-backports/universe/dep11/Components-amd64.yml.xz](http://br.archive.ubuntu.com/ubuntu/dists/focal-backports/universe/dep11/Components-amd64.yml.xz)  Hash Sum mismatch
   Hashes of expected file:
    - Filesize:10328 [weak]
    - SHA256:3566fd2912a25cd3d01b230acbaa51e61b4e99f1b984fdd1eac52125c4daea68
    - SHA1:6e704c7a3840db937c83681785a9a716898897e3 [weak]
    - MD5Sum:74d117d81a79fa52fdf1a1a1449582b8 [weak]
   Hashes of received file:
    - SHA256:b00a4fd108011f79a78816ef00f7070dccb21465f8fd61fcc88e56d86315ab1c
    - SHA1:dd4b3f85ec6159216b133c9426c8010bf98caa47 [weak]
    - MD5Sum:cac480dddf202b846c2b322587c99447 [weak]
    - Filesize:10328 [weak]
   Last modification reported: Sat, 17 Jul 2021 07:22:09 +0000
   Release file created at: Sat, 17 Jul 2021 11:20:47 +0000
E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by mikewhatever on 2021-07-17
How do you know it's a "potential security breach"? Just wait a while for the sync to complete, then try again.

PS: Grey fonts on grey background is a waist of our time.

---

### Post by ricleite on 2021-07-17
[FONT=DDG_ProximaNova]Me perdoe! Provavelmente minha extensão do Chrome, de alguma forma mudou de cor. ( [https://mybrowseraddon.com/dark-mode.html](https://mybrowseraddon.com/dark-mode.html) ) Eu havia lido por engano o tamanho dos arquivos, provavelmente meu cansaço extremo, e parecia que o arquivo era maior do que o correto. Este comportamento pode ser uma tentativa de alteração maliciosa. Obrigado pela sua resposta![/FONT]

---

### Post by MAFoElffen on 2021-07-17
> **ricleite said:**
> [FONT=DDG_ProximaNova]Forgive me! Probably my Chrome extension has somehow changed color. ( [https://mybrowseraddon.com/dark-mode.html](https://mybrowseraddon.com/dark-mode.html) ) I had mistakenly read the file sizes, probably my extreme fatigue, and it looked like the file was bigger than correct. This behavior could be a malicious alteration attempt. Thanks for your response! ![/FONT]

So did you try to do this again later?

---

