---
title: "Not able to do-release-upgrade"
date: 2022-05-04
forum: Installation &amp; Upgrades
---

### Post by 8a512s78k0kg on 2022-05-04
Hello,

I am trying to update my Server to the latest LTS version from Ubuntu server 20.10.

when i do-release-updgrade, I get:[INDENT][COLOR=#696969]Checking for a new Ubuntu release
Your Ubuntu release is not supported anymore.
For upgrade information, please visit:
[http://www.ubuntu.com/releaseendoflife](http://www.ubuntu.com/releaseendoflife)

Please install all available updates for your release before upgrading.[/COLOR]
[/INDENT]

OK fair enough, let's try **sudo apt-get full-upgrade**:
[INDENT][COLOR=#696969]sudo apt full-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  linux-firmware
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 124 MB of archives.
After this operation, 1,449 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Err:1 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) groovy-updates/main arm64 linux-firmware all 1.190.6
  404  Not Found [IP: 185.125.190.39 80]
E: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/pool/main/l/linux-firmware/linux-firmware_1.190.6_all.deb](http://ports.ubuntu.com/ubuntu-ports/pool/main/l/linux-firmware/linux-firmware_1.190.6_all.deb)  404  Not Found [IP: 185.125.190.39 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?[/COLOR]
[/INDENT]


...Ok this time with sudo **apt-get full-upgrade --fix-missing**:
[INDENT][COLOR=#696969]sudo apt full-upgrade --fix-missing
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  linux-firmware
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 124 MB of archives.
After this operation, 1,449 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Err:1 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) groovy-updates/main arm64 linux-firmware all 1.190.6
  404  Not Found [IP: 185.125.190.36 80]
E: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/pool/main/l/linux-firmware/linux-firmware_1.190.6_all.deb](http://ports.ubuntu.com/ubuntu-ports/pool/main/l/linux-firmware/linux-firmware_1.190.6_all.deb)  404  Not Found [IP: 185.125.190.36 80]

[/COLOR][/INDENT]

I'm losing my mind at this point. **Sudo apt update**??
[INDENT][COLOR=#696969]Ign:1 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) groovy InRelease
Ign:2 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) groovy-updates InRelease
Ign:3 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) groovy-backports InRelease
Ign:4 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) groovy-security InRelease
Err:5 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) groovy Release
  404  Not Found [IP: 185.125.190.36 80]
Err:6 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) groovy-updates Release
  404  Not Found [IP: 185.125.190.36 80]
Err:7 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) groovy-backports Release
  404  Not Found [IP: 185.125.190.36 80]
Err:8 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) groovy-security Release
  404  Not Found [IP: 185.125.190.36 80]
Reading package lists... Done
E: The repository 'http://ports.ubuntu.com/ubuntu-ports groovy Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ports.ubuntu.com/ubuntu-ports groovy-updates Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ports.ubuntu.com/ubuntu-ports groovy-backports Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ports.ubuntu.com/ubuntu-ports groovy-security Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
[/COLOR][/INDENT]


OK but how about **sudo apt-get update -y**:
[INDENT][COLOR=#696969]sudo apt-get update -y
Ign:1 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) groovy InRelease
Ign:2 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) groovy-updates InRelease
Ign:3 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) groovy-backports InRelease
Ign:4 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) groovy-security InRelease
Err:5 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) groovy Release
  404  Not Found [IP: 185.125.190.39 80]
Err:6 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) groovy-updates Release
  404  Not Found [IP: 185.125.190.39 80]
Err:7 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) groovy-backports Release
  404  Not Found [IP: 185.125.190.39 80]
Err:8 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) groovy-security Release
  404  Not Found [IP: 185.125.190.39 80]
Reading package lists... Done
E: The repository 'http://ports.ubuntu.com/ubuntu-ports groovy Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ports.ubuntu.com/ubuntu-ports groovy-updates Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ports.ubuntu.com/ubuntu-ports groovy-backports Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ports.ubuntu.com/ubuntu-ports groovy-security Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
[/COLOR][/INDENT]
[INDENT][COLOR=#696969]N: See apt-secure(8) manpage for repository creation and user configuration details.

[/COLOR][/INDENT]


As you call can see **this has not been going very well**. Have any suggestions for what I should try to get this server on the latest version?

---

### Post by guiverc on 2022-05-04
Ubuntu 20.10 was the 2020-October release of Ubuntu, which had 9 months of supported life.  It's now EOL (*end-of-life*).

[https://fridge.ubuntu.com/2021/07/25/ubuntu-20-10-groovy-gorilla-end-of-life-reached-on-july-22-2021/](https://fridge.ubuntu.com/2021/07/25/ubuntu-20-10-groovy-gorilla-end-of-life-reached-on-july-22-2021/)

The *release-upgrade* path from 20.10 was to the next release; ie. 21.04, however that was gone with [21.04 reached EOL]("https://fridge.ubuntu.com/2022/01/21/ubuntu-21-04-hirsute-hippo-end-of-life-reached-on-january-20-2022/").

If you need a longer supported life; use a LTS or *long term support* release; which are the first release(s) of the even year; ie. 20.04 for 2020, and 22.04 for 2022.  Knowing the end-of-life is rather easy; 20.10 (2020-October) + 9 months = 2021-July, or alternatively it's always 3 months after the next release (21.04 + 3 months = 2021-July)

The [EOLUpgrades]("https://help.ubuntu.com/community/EOLUpgrades") link is usually helpful; but not as much with *ports*, of which I have little experience sorry.

There is no upgrade path from 20.10 to the next LTS; it had only the single QA-tested & *supported* upgrade path being to the next release of Ubuntu 21.04.  An LTS install can upgrade to the next release OR next-LTS; non-LTS upgrades to the next release.

---

### Post by Impavidus on 2022-05-05
Your server hasn't received any updates for 10 months. 20.10 is no longer supported; that's why apt update and friends give errors. You could try an EOL upgrade (link in above post), which is a slow and error-prone way to get to 21.04. 21.04 is dead too, so you need another EOL upgrade to 21.10 and then a regular upgrade to 22.04. I recommend a fresh install.

I don't know about arm64 ports specifically, but the above is true for all variants of Ubuntu. Except that I don't know whether the EOL upgrades can be done in the same way.

It's better to upgrade before your current version goes EOL. For servers, it's usually better to stick to LTS versions, unless your hardware really requires the interim version.

---

### Post by 8a512s78k0kg on 2022-05-06
Thanks so much for letting me know this!! I did a custom upgrade and was able to get my server running the latest release version. I appreciate the help :)

---

