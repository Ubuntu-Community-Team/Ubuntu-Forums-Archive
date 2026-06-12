---
title: "unattended-upgrades does no update"
date: 2017-09-29
forum: Installation &amp; Upgrades
---

### Post by mlohr on 2017-09-29
Hey,

i have a virtual server running and tried to enable unattended-upgrades - and have no idea why i'm not successful. I know there are new packages, i can see unattended-upgrades running in the logs (every night) but the packages still got not upgraded. After running apt-get update manually, unattended-upgrade will do the upgrade. So, how can i unattended-upgrades let do apt-get update, too? There are plenty of tutorials out with files like "10periodic", "20auto-upgrades" and "50unattended-upgrades". My current state:

10periodic:
```

APT::Periodic::Enable "1";
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "1";
APT::Periodic::Unattended-Upgrade "1";

```

20auto-upgrades:
```

APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Unattended-Upgrade "1";

```

There are also some other examples with using 02periodic as file name. Does the file name matters? What am i doing wrong?

Thanks for your help...

Best regards
Matthias

---

### Post by ian-weisser on 2017-09-29
1) Let's see if unattended-upgrades is really running.
Please show us the complete output of the following command:
```
ls -la /var/lib/apt/periodic
```

2) What do your logs in /var/log/unattended-upgrades say?
Can you please show us one day's run of u-u logs?

3) Pick two or three packages that are not getting upgraded. Which repositories are they in?
If you're not sure, show us the result of the following command for each package:
```
apt show $PACKAGE_NAME | grep APT-Sources
```

---

### Post by mlohr on 2017-09-29
ls -la /var/lib/apt/periodic:
```

total 8
drwxr-xr-x 2 root root 4096 Sep 21 08:50 .
drwxr-xr-x 6 root root 4096 Sep 26 10:49 ..
-rw-r--r-- 1 root root    0 Sep 29 06:46 unattended-upgrades-stamp
-rw-r--r-- 1 root root    0 Sep 21 08:50 update-stamp
-rw-r--r-- 1 root root    0 Sep 29 06:46 upgrade-stamp

```

log:
```

2017-09-26 06:12:19,749 INFO Initial blacklisted packages: 
2017-09-26 06:12:19,750 INFO Initial whitelisted packages: 
2017-09-26 06:12:19,750 INFO Starting unattended upgrades script
2017-09-26 06:12:19,750 INFO Allowed origins are: ['o=Ubuntu,a=xenial', 'o=Ubuntu,a=xenial-security', 'o=*packages.gitlab.com/gitlab/gitlab-ce,a=xenial', 'o=UbuntuESM,a=xenial']
2017-09-26 06:12:22,928 INFO No packages found that can be upgraded unattended and no pending auto-removals
2017-09-26 10:48:02,500 INFO Initial blacklisted packages: 
2017-09-26 10:48:02,501 INFO Initial whitelisted packages: 
2017-09-26 10:48:02,501 INFO Starting unattended upgrades script
2017-09-26 10:48:02,501 INFO Allowed origins are: ['o=Ubuntu,a=xenial', 'o=Ubuntu,a=xenial-security', 'o=*packages.gitlab.com/gitlab/gitlab-ce,a=xenial', 'o=UbuntuESM,a=xenial']
2017-09-26 10:48:06,054 INFO No packages found that can be upgraded unattended and no pending auto-removals
2017-09-26 10:48:28,511 INFO Initial blacklisted packages: 
2017-09-26 10:48:28,511 INFO Initial whitelisted packages: 
2017-09-26 10:48:28,524 INFO Starting unattended upgrades script
2017-09-26 10:48:28,524 INFO Allowed origins are: ['o=Ubuntu,a=xenial', 'o=Ubuntu,a=xenial-security', 'o=*packages.gitlab.com/gitlab/gitlab-ce,a=xenial', 'o=UbuntuESM,a=xenial']
2017-09-26 10:48:31,837 INFO No packages found that can be upgraded unattended and no pending auto-removals
2017-09-26 10:48:56,174 INFO Initial blacklisted packages: 
2017-09-26 10:48:56,175 INFO Initial whitelisted packages: 
2017-09-26 10:48:56,175 INFO Starting unattended upgrades script
2017-09-26 10:48:56,175 INFO Allowed origins are: ['o=Ubuntu,a=xenial', 'o=Ubuntu,a=xenial-security', 'o=*packages.gitlab.com/gitlab/gitlab-ce,a=xenial', 'o=UbuntuESM,a=xenial']
2017-09-26 10:49:37,966 INFO Packages that will be upgraded: gitlab-ce libwbclient0 python-samba samba samba-common samba-common-bin samba-libs
2017-09-26 10:49:37,969 INFO Writing dpkg log to '/var/log/unattended-upgrades/unattended-upgrades-dpkg.log'
2017-09-26 11:03:04,608 INFO All upgrades installed
2017-09-27 06:57:43,980 INFO Initial blacklisted packages: 
2017-09-27 06:57:43,981 INFO Initial whitelisted packages: 
2017-09-27 06:57:43,982 INFO Starting unattended upgrades script
2017-09-27 06:57:43,982 INFO Allowed origins are: ['o=Ubuntu,a=xenial', 'o=Ubuntu,a=xenial-security', 'o=*packages.gitlab.com/gitlab/gitlab-ce,a=xenial', 'o=UbuntuESM,a=xenial']
2017-09-27 06:57:47,352 INFO No packages found that can be upgraded unattended and no pending auto-removals
2017-09-28 06:43:55,594 INFO Initial blacklisted packages: 
2017-09-28 06:43:55,595 INFO Initial whitelisted packages: 
2017-09-28 06:43:55,595 INFO Starting unattended upgrades script
2017-09-28 06:43:55,595 INFO Allowed origins are: ['o=Ubuntu,a=xenial', 'o=Ubuntu,a=xenial-security', 'o=*packages.gitlab.com/gitlab/gitlab-ce,a=xenial', 'o=UbuntuESM,a=xenial']
2017-09-28 06:43:59,084 INFO No packages found that can be upgraded unattended and no pending auto-removals
2017-09-29 06:46:55,610 INFO Initial blacklisted packages: 
2017-09-29 06:46:55,610 INFO Initial whitelisted packages: 
2017-09-29 06:46:55,611 INFO Starting unattended upgrades script
2017-09-29 06:46:55,611 INFO Allowed origins are: ['o=Ubuntu,a=xenial', 'o=Ubuntu,a=xenial-security', 'o=*packages.gitlab.com/gitlab/gitlab-ce,a=xenial', 'o=UbuntuESM,a=xenial']
2017-09-29 06:46:59,115 INFO No packages found that can be upgraded unattended and no pending auto-removals

```

gitlab-ce package:
```

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.


APT-Sources: https://packages.gitlab.com/gitlab/gitlab-ce/ubuntu xenial/main amd64 Packages

```

Tested right now:
[LIST]
[*]unattended-upgrades -d states "No packages found that can be upgraded unattended and no pending auto-removals".
[*]called apt-get update
[*]now unattended-upgrades would try to update the gitlab-ce package - but only if i run apt-get update manually. Shouln't that be done by unattended-upgrades, too?
[/LIST]

---

### Post by ian-weisser on 2017-09-29
Ah, you must merely change the repository settings. U-U seems to be working just fine.

Unattended-upgrade, by default, is set to ONLY upgrade from Ubuntu's -security repository.
This is a deliberately conservative choice, to keep U-U from installing unreliable (or poisoned!) upgrades from elsewhere upon the dirty, untrustworthy internet.

To extend your trust to the gitlab repository, you must edit /etc/apt/apt.conf.d/50unattended-upgrades (as sudo).
Look around lines 5-15 (or so) for the trusted repositories:
```
Unattended-Upgrade::Allowed-Origins {
        "${distro_id}:${distro_codename}";
        "${distro_id}:${distro_codename}-security";
//      "${distro_id}:${distro_codename}-updates";
//      "${distro_id}:${distro_codename}-proposed";
//      "${distro_id}:${distro_codename}-backports";
};
```
Add a line (uncommented, of course), for your repository and release. See [https://askubuntu.com/questions/87849](https://askubuntu.com/questions/87849) for how to locate the Origin and Suite using the 'apt show' command.
You don't need to reboot. Changes will be effective upon saving. You can run U-U immediately from the command line ($ unattended-upgrade) to test.

---

### Post by mlohr on 2017-09-29
I already tried that... without success ;)

/var/lib/apt/lists/packages.gitlab.com_gitlab_gitlab-ce_ubuntu_dists_xenial_InRelease:
```

Origin: packages.gitlab.com/gitlab/gitlab-ce
Label: gitlab-ce
Date: Thu, 28 Sep 2017 02:15:26 +0000
Suite: xenial
Codename: xenial
Version: 1
Components: main
Architectures: amd64 armel armhf i386 ia64 mips mipsel powerpc ppc64el s390 s390x sparc alpha avr32 hppa m32 m68k sh arm64
Description: APT/YUM repository for GitLab Community Edition packages
Acquire-By-Hash: yes

```

My /etc/apt/apt.conf.d/50unattended-upgrades looks like (found here:[https://forum.gitlab.com/t/upgrade-via-unattended-upgrades/6120/3]("https://forum.gitlab.com/t/upgrade-via-unattended-upgrades/6120/3")
```
Unattended-Upgrade::Allowed-Origins {
        "${distro_id}:${distro_codename}";
        "${distro_id}:${distro_codename}-security";
        "*packages.gitlab.com/gitlab/gitlab-ce:${distro_codename}";.
        "${distro_id}ESM:${distro_codename}";
};

[...]

```[COLOR=#000000]

output from unattended-upgrades -d (before manually running apt-get update), and the gitlab part is listed:
[/COLOR]```
Initial blacklisted packages: 
Initial whitelisted packages: 
Starting unattended upgrades script
Allowed origins are: ['o=Ubuntu,a=xenial', 'o=Ubuntu,a=xenial-security', 'o=*packages.gitlab.com/gitlab/gitlab-ce,a=xenial', 'o=UbuntuESM,a=xenial']
adjusting candidate version: 'libapparmor1=2.10.95-0ubuntu2.6'
adjusting candidate version: 'libcryptsetup4=2:1.6.6-5ubuntu2'
adjusting candidate version: 'libplymouth4=0.9.2-3ubuntu13'
adjusting candidate version: 'libpython3.5=3.5.2-2ubuntu0~16.04.1'
adjusting candidate version: 'libpython3.5-minimal=3.5.2-2ubuntu0~16.04.1'
adjusting candidate version: 'libpython3.5-stdlib=3.5.2-2ubuntu0~16.04.1'
adjusting candidate version: 'plymouth=0.9.2-3ubuntu13'
adjusting candidate version: 'python3.5=3.5.2-2ubuntu0~16.04.1'
adjusting candidate version: 'python3.5-minimal=3.5.2-2ubuntu0~16.04.1'
pkgs that look like they should be upgraded: 
Fetched 0 B in 0s (0 B/s)                                                                                                                                                                                         
fetch.run() result: 0
blacklist: []
whitelist: []
No packages found that can be upgraded unattended and no pending auto-removals

```[COLOR=#000000]

But as i said: After running apt-get update manually, unattended-upgrades will also try to update gitlab-ce.[/COLOR]

---

### Post by ian-weisser on 2017-09-29
Well you're right, and I did overlook apt-update-not-running-automatically.
It's plain to see right there among your timestamps, too.
Sorry I missed that! That's unusual. I must think about why apt update doesn't work  from U-U but does work manually.

---

