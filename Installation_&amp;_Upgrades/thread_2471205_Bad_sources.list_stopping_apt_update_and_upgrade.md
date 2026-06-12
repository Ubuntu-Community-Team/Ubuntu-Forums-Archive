---
title: "Bad sources.list stopping apt update and upgrade"
date: 2022-01-23
forum: Installation &amp; Upgrades
---

### Post by cjb on 2022-01-23
I'm trying to move from 21.04 desktop to 21.10 (long time since I used Ubuntu and I hadn't realised what the upgrade schedule looks like, so I was caught out).

The instructions I saw online ([https://butlerraines.com/code-stuff/upgrading-end-life-eol-ubuntu-version-ubuntu-1904](https://butlerraines.com/code-stuff/upgrading-end-life-eol-ubuntu-version-ubuntu-1904) and others similar) all started by doing an apt update. Using either apt or apt-get, running an update process fails with a message like this, repeated four times:


```
Err:13 http://old-releases.ubuntu.com/ubuntu hirsute Release
  404  Not Found [IP: 2001:67c:1562::25 80]

...

E: The repository 'http://old-releases.ubuntu.com/ubuntu hirsute Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

The message repeats with "hirsute-updates", "hirsute-backports", and "hirsute-security" in place of "hirsute".

The uncommented parts of my /etc/apt/sources.list file are here:


```
deb http://old-releases.ubuntu.com/ubuntu/ hirsute main restricted
deb http://old-releases.ubuntu.com/ubuntu/ hirsute-updates main restricted
deb http://old-releases.ubuntu.com/ubuntu/ hirsute universe
deb http://old-releases.ubuntu.com/ubuntu/ hirsute-updates universe
deb http://old-releases.ubuntu.com/ubuntu/ hirsute multiverse
deb http://old-releases.ubuntu.com/ubuntu/ hirsute-updates multiverse
deb http://old-releases.ubuntu.com/ubuntu/ hirsute-backports main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ hirsute-security main restricted
deb http://old-releases.ubuntu.com/ubuntu/ hirsute-security universe
deb http://old-releases.ubuntu.com/ubuntu/ hirsute-security multiverse
```

I thought that once a release had reached EOL, its package list was moved to old-releases.ubuntu.com, and I could at least complete an update using those URLs. Am I mistaken? Is there some other step I need to complete first, or is it not possible to complete an upgrade at all once a release is EOL? Or do I just need to wait a couple of days for the package lists to be moved?

---

### Post by guiverc on 2022-01-23
The *end-of-life* release [announcements for Ubuntu 21.04]("https://fridge.ubuntu.com/2022/01/21/ubuntu-21-04-hirsute-hippo-end-of-life-reached-on-january-20-2022/") state

> As of January 20, 2022, Ubuntu 21.04 is no longer supported. No more  package updates will be accepted to 21.04, and **it will be archived to  old-releases.ubuntu.com in the coming weeks.**

ie. the *move* it said would occur, likely won't have happened when you tried; it's only *days* after the EOL rather than *weeks*.

You should return your *old-releases.ubuntu.com* back to *archive.ubuntu.com *and use the commands to upgrade you provided in the documentation.; ie. read [https://help.ubuntu.com/community/ImpishUpgrades](https://help.ubuntu.com/community/ImpishUpgrades) which was in the page I provided earlier.

---

### Post by cjb on 2022-01-24
Solved, thank you! Now running impish.

Two things I hadn't realised:

- a "kept back" upgrade on an application package was sufficient to block the OS upgrade.
- archive.ubuntu.com is a thing. I thought the package lists were temporarily unavailable after disappearing from the country-specific mirror I was using.

---

