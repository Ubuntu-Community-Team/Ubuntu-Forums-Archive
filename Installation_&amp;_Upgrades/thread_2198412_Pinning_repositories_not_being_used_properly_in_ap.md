---
title: "Pinning repositories not being used properly in apt-get dist-upgrade -s"
date: 2014-01-08
forum: Installation &amp; Upgrades
---

### Post by lieutdan13 on 2014-01-08
I'm having a unique issue involving apt pinning and apt-get reporting an incorrect repository. There is a package that has the same version in 2 different repositories (precise-updates and precise-security). Even though I have the Apt Pinning/Preferences configured properly and **apt-cache policy** reporting the correct information, **apt-get dist-upgrade -s** is not reporting the correct repository. This becomes an issue when trying to determine if a package/version is a security update or not.

```

root@server:~# cat /etc/apt/preferences.d/pin-precise-updates-release
Package: *
Pin: release a=precise-updates
Pin-Priority: 600


Package: *
Pin: release a=precise
Pin-Priority: 300


root@server:~# cat /etc/apt/preferences.d/pin-precise-security-release
Package: *
Pin: release a=precise-security
Pin-Priority: 900

root@server:~# sudo apt-get update
(output clipped)

root@server:~# sudo apt-cache policy linux-libc-dev
linux-libc-dev:
  Installed: 3.2.0-53.81
  Candidate: 3.2.0-58.88
  Version table:
     3.2.0-58.88 0
        600 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main amd64 Packages
        900 http://security.ubuntu.com/ubuntu/ precise-security/main amd64 Packages
 *** 3.2.0-53.81 0
        100 /var/lib/dpkg/status
     3.2.0-23.36 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages


root@server:~# sudo apt-get dist-upgrade -s
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  linux-libc-dev
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Inst linux-libc-dev [3.2.0-53.81] (3.2.0-58.88 Ubuntu:12.04/precise-updates [amd64])
Conf linux-libc-dev (3.2.0-58.88 Ubuntu:12.04/precise-updates [amd64])

```

I would expect the last command to show **Ubuntu:12.04/precise-security** and not **Ubuntu:12.04/precise-updates** because of the higher repository priority. I have also found that if I put the precise-security source before precise-updates in /etc/apt/sources.list, **apt-get dist-upgrade -s** shows the **precise-security** repository.

Any ideas as to why this is happening?

---

### Post by lieutdan13 on 2014-01-10
Is anyone else seeing the same thing? I'm seeing this on 10+ of my Ubuntu 12.04 LTS servers. I'm not sure if this is a apt-get bug, Ubuntu bug, or something else. If anyone else is seeing this, I will open a bug.

---

