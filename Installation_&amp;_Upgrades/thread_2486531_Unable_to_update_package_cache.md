---
title: "Unable to update package cache"
date: 2023-05-03
forum: Installation &amp; Upgrades
---

### Post by andrell10 on 2023-05-03
[FONT=Arial]Hello I´m new to Linux Ubuntu and I trying to install Pi-Hole[/FONT]
[FONT=Arial]When I do:[/FONT]

[COLOR=var(--hljs-attribute)]curl[/COLOR] -sSL [https://install.pi-hole.net](https://install.pi-hole.net) | bash
[FONT=Arial]or the other 2 alternatives I get this error:
[/FONT]

[COLOR=var(--hljs-symbol)]Error:[/COLOR] Unable [COLOR=var(--primary-very-high)]**to**[/COLOR] update package cache. Please [COLOR=var(--primary-very-high)]**try**[/COLOR] [COLOR=var(--hljs-string)]"sudo apt update"

[FONT=Arial]And when I try the sudo apt update I get this:
[/FONT][/COLOR][FONT=Consolas]
E: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/jammy-updates/main/dep11/Components-amd64.yml.xz](http://br.archive.ubuntu.com/ubuntu/dists/jammy-updates/main/dep11/Components-amd64.yml.xz) File has unexpected size (101328 != 101404). Mirror sync in progress? [IP: 200.236.31.4 80][/FONT] Hashes of expected file:
- Filesize:101404 [weak]
- SHA256:fa2cad397e3e929f201dcffd0a2fa2daf40ec50541fa92f5bcfff547465bbd4a
- SHA1:5815ba91315d62b854ae46086560f92e5b58ca50 [weak]
- MD5Sum:df05be48c08f9fb6eff44b0bcf76325d [weak]
Release file created at: Tue, 02 May 2023 22:13:54 +0000
E: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/jammy-updates/universe/dep11/Components-amd64.yml.xz](http://br.archive.ubuntu.com/ubuntu/dists/jammy-updates/universe/dep11/Components-amd64.yml.xz)
E: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/jammy-updates/multiverse/dep11/Components-amd64.yml.xz](http://br.archive.ubuntu.com/ubuntu/dists/jammy-updates/multiverse/dep11/Components-amd64.yml.xz)
E: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/jammy-backports/main/dep11/Components-amd64.yml.xz](http://br.archive.ubuntu.com/ubuntu/dists/jammy-backports/main/dep11/Components-amd64.yml.xz) Hash Sum mismatch
Hashes of expected file:
- Filesize:7976 [weak]
- SHA256:b4f806ef7207456e072e1cd7b558a0b6d41a1a0e96fb150b3abd5c31d60cde74
- SHA1:cabf8a4384f9175f827c24ed429cf87b85799d29 [weak]
- MD5Sum:27f5062dd83152a536cc229e3bdea4ae [weak]
Hashes of received file:
- SHA256:a815d6bc8df2dd4a1b2c0c01e81b395c7567b2689dc72d0cb556973f15bfc93f
- SHA1:c2344fc6b8b78a5a4958ee933082140f625bc527 [weak]
- MD5Sum:02736e134538cd7a4c3d29f38d3cb549 [weak]
- Filesize:7976 [weak]
Last modification reported: Tue, 02 May 2023 14:43:32 +0000
Release file created at: Tue, 02 May 2023 22:14:38 +0000
E: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/jammy-backports/universe/dep11/Components-amd64.yml.xz](http://br.archive.ubuntu.com/ubuntu/dists/jammy-backports/universe/dep11/Components-amd64.yml.xz)
[COLOR=var(--hljs-string)][FONT=Consolas]E: Some index files failed to download. They have been ignored, or old ones used instead.[/FONT][FONT=Arial]

[/FONT][/COLOR]

---

