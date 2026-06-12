---
title: "Changing the sources for updates"
date: 2019-10-02
forum: Installation &amp; Upgrades
---

### Post by usableusername on 2019-10-02
Hi, I wanted to know how I would go about changing the sources used for updates? I'm using Odroid n2 with ubunut's MATE OS for ARM devices, and I get 404 errors when I try to install from the sources provided to me.

[FONT=Arial]```
root@odroid:/home/odroid# apt update
```[/FONT]```

[FONT=Arial]Hit:1 [/FONT][http://apt.connectify.me]("http://apt.connectify.me/")[FONT=Arial] speedify InRelease[/FONT]
[FONT=Arial]Hit:3 [/FONT][http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports)[FONT=Arial] bionic-security InRelease[/FONT]
[FONT=Arial]Hit:4 [/FONT][http://deb.odroid.in/n2](http://deb.odroid.in/n2)[FONT=Arial] bionic InRelease[/FONT]
[FONT=Arial]Get:5 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-updates InRelease [88.7 kB][/FONT]
[FONT=Arial]Hit:6 [/FONT][http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)[FONT=Arial] bionic InRelease[/FONT]
[FONT=Arial]Get:8 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-security InRelease [88.7 kB][/FONT]
[FONT=Arial]Get:2 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic InRelease [242 kB][/FONT]
[FONT=Arial]Get:7 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-backports InRelease [74.6 kB][/FONT]
[FONT=Arial]Get:9 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-updates/main Sources [292 kB][/FONT]
[FONT=Arial]Get:10 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-updates/multiverse Sources [4996 B][/FONT]
[FONT=Arial]Get:11 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-updates/universe Sources [263 kB][/FONT]
[FONT=Arial]Get:12 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-updates/restricted Sources [4116 B][/FONT]
[FONT=Arial]Get:13 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-updates/main arm64 Packages [568 kB][/FONT]
[FONT=Arial]Get:13 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-updates/main arm64 Packages [568 kB][/FONT]
[FONT=Arial]Get:13 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-updates/main arm64 Packages [568 kB][/FONT]
[FONT=Arial]Get:13 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-updates/main arm64 Packages [568 kB][/FONT]
[FONT=Arial]Get:13 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-updates/main arm64 Packages [568 kB][/FONT]
[FONT=Arial]Get:13 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-updates/main arm64 Packages [568 kB][/FONT]
[FONT=Arial]Get:13 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-updates/main arm64 Packages [568 kB][/FONT]
[FONT=Arial]Get:13 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-updates/main arm64 Packages [568 kB][/FONT]
[FONT=Arial]Get:13 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-updates/main arm64 Packages [568 kB][/FONT]
[FONT=Arial]Get:13 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-updates/main arm64 Packages [568 kB][/FONT]
[FONT=Arial]Get:13 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-updates/main arm64 Packages [568 kB][/FONT]
[FONT=Arial]Get:13 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-updates/main arm64 Packages [568 kB][/FONT]
[FONT=Arial]Get:13 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-updates/main arm64 Packages [568 kB][/FONT]
[FONT=Arial]Ign:13 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-updates/main arm64 Packages[/FONT]
[FONT=Arial]Get:27 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-updates/restricted arm64 Packages [956 B][/FONT]
[FONT=Arial]Get:27 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-updates/restricted arm64 Packages [956 B][/FONT]
[FONT=Arial]Get:27 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-updates/restricted arm64 Packages [956 B][/FONT]
[FONT=Arial]Ign:27 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-updates/restricted arm64 Packages[/FONT]
[FONT=Arial]Ign:31 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-updates/universe arm64 Packages[/FONT]
[FONT=Arial]Ign:32 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-updates/multiverse arm64 Packages[/FONT]
[FONT=Arial]Ign:33 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic/main arm64 Packages[/FONT]
[FONT=Arial]Ign:34 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic/restricted arm64 Packages[/FONT]
[FONT=Arial]Ign:35 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic/universe arm64 Packages[/FONT]
[FONT=Arial]Ign:36 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic/multiverse arm64 Packages[/FONT]
[FONT=Arial]Ign:37 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-backports/main arm64 Packages[/FONT]
[FONT=Arial]Ign:38 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-backports/universe arm64 Packages[/FONT]
[FONT=Arial]Ign:13 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-updates/main arm64 Packages[/FONT]
[FONT=Arial]Ign:27 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-updates/restricted arm64 Packages[/FONT]
[FONT=Arial]Ign:31 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-updates/universe arm64 Packages[/FONT]
[FONT=Arial]Ign:32 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-updates/multiverse arm64 Packages[/FONT]
[FONT=Arial]Ign:33 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic/main arm64 Packages[/FONT]
[FONT=Arial]Ign:34 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic/restricted arm64 Packages[/FONT]
[FONT=Arial]Ign:35 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic/universe arm64 Packages[/FONT]
[FONT=Arial]Ign:36 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic/multiverse arm64 Packages[/FONT]
[FONT=Arial]Ign:37 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-backports/main arm64 Packages[/FONT]
[FONT=Arial]Ign:38 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-backports/universe arm64 Packages[/FONT]
[FONT=Arial]Ign:13 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-updates/main arm64 Packages[/FONT]
[FONT=Arial]Ign:27 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-updates/restricted arm64 Packages[/FONT]
[FONT=Arial]Ign:31 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-updates/universe arm64 Packages[/FONT]
[FONT=Arial]Ign:32 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-updates/multiverse arm64 Packages[/FONT]
[FONT=Arial]Ign:33 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic/main arm64 Packages[/FONT]
[FONT=Arial]Ign:34 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic/restricted arm64 Packages[/FONT]
[FONT=Arial]Ign:35 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic/universe arm64 Packages[/FONT]
[FONT=Arial]Ign:36 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic/multiverse arm64 Packages[/FONT]
[FONT=Arial]Ign:37 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-backports/main arm64 Packages[/FONT]
[FONT=Arial]Ign:38 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-backports/universe arm64 Packages[/FONT]
[FONT=Arial]Err:13 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-updates/main arm64 Packages[/FONT]
[FONT=Arial]404 Not Found [IP: 91.189.91.24 80][/FONT]
[FONT=Arial]Ign:27 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-updates/restricted arm64 Packages[/FONT]
[FONT=Arial]Ign:31 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-updates/universe arm64 Packages[/FONT]
[FONT=Arial]Ign:32 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-updates/multiverse arm64 Packages[/FONT]
[FONT=Arial]Err:33 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic/main arm64 Packages[/FONT]
[FONT=Arial]404 Not Found [IP: 91.189.91.24 80][/FONT]
[FONT=Arial]Ign:34 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic/restricted arm64 Packages[/FONT]
[FONT=Arial]Ign:35 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic/universe arm64 Packages[/FONT]
[FONT=Arial]Ign:36 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic/multiverse arm64 Packages[/FONT]
[FONT=Arial]Err:37 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-backports/main arm64 Packages[/FONT]
[FONT=Arial]404 Not Found [IP: 91.189.91.24 80][/FONT]
[FONT=Arial]Ign:38 [/FONT][http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu)[FONT=Arial] bionic-backports/universe arm64 Packages[/FONT]
[FONT=Arial]Fetched 494 kB in 14s (35.3 kB/s)[/FONT]
[FONT=Arial]Reading package lists... Done[/FONT]
[FONT=Arial]E: Failed to fetch [/FONT][http://uk.archive.ubuntu.com/ubuntu/dists/bionic-updates/main/binary-arm64/Packages](http://uk.archive.ubuntu.com/ubuntu/dists/bionic-updates/main/binary-arm64/Packages)[FONT=Arial] 404 Not Found [IP: 91.189.91.24 80][/FONT]
[FONT=Arial]E: Failed to fetch [/FONT][http://uk.archive.ubuntu.com/ubuntu/dists/bionic/main/binary-arm64/Packages](http://uk.archive.ubuntu.com/ubuntu/dists/bionic/main/binary-arm64/Packages)[FONT=Arial] 404 Not Found [IP: 91.189.91.24 80][/FONT]
[FONT=Arial]E: Failed to fetch [/FONT][http://uk.archive.ubuntu.com/ubuntu/dists/bionic-backports/main/binary-arm64/Packages](http://uk.archive.ubuntu.com/ubuntu/dists/bionic-backports/main/binary-arm64/Packages)[FONT=Arial] 404 Not Found [IP: 91.189.91.24 80][/FONT]
[FONT=Arial]E: Some index files failed to download. They have been ignored, or old ones used instead.[/FONT]
```
[FONT=Arial]
[/FONT]```
[FONT=Arial]root@odroid:/home/odroid# apt install lsof[/FONT]
``````

[FONT=Arial]Reading package lists... Done[/FONT]
[FONT=Arial]Building dependency tree[/FONT]
[FONT=Arial]Reading state information... Done[/FONT]
[FONT=Arial]Package lsof is not available, but is referred to by another package.[/FONT]
[FONT=Arial]This may mean that the package is missing, has been obsoleted, or[/FONT]
[FONT=Arial]is only available from another source[/FONT]

[FONT=Arial]E: Package 'lsof' has no installation candidate[/FONT]
```

---

### Post by QIII on 2019-10-02
Since I am getting the Apache default page for that URL (indicating that it does exist), I suspect that either:  Work is being done or work was done and someone forgot to clean up and restart.

When I get those sorts of things out of the blue for repos I've been using regularly,  I usually first wait an hour or two before going through the drill of modifying sources.

---

### Post by usableusername on 2019-10-02
Ok, thanks for the reply. It's been like this for about 2-3 days now, so I hope no one fell into a coma, lol.

---

