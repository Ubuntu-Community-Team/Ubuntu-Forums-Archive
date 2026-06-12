---
title: "Broken dependency caused by ESM repository trusty-infra-security"
date: 2021-10-22
forum: Installation &amp; Upgrades
---

### Post by daku8938 on 2021-10-22
I have an Ubuntu 14.04 Trusty server, fully updated, with the following apt config including Ubuntu Advantage ESM support:

[FONT=courier new]/etc/apt/sources.list[/FONT]:
```

deb         [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/)        trusty                  main restricted universe multiverse
deb         [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu)           trusty-security         main restricted universe multiverse

```
[FONT=courier new]/etc/apt/sources.list.d/ubuntu-esm-infra-trusty.list[/FONT]:
```

deb [https://esm.ubuntu.com/ubuntu](https://esm.ubuntu.com/ubuntu) trusty-infra-security main

```
For having unattended-upgrade being able to automatically reboot if needed, according to this article [https://help.ubuntu.com/community/AutomaticSecurityUpdates](https://help.ubuntu.com/community/AutomaticSecurityUpdates)
I *'need to have the "update-notifier-common" package installed'*.

But unfortunately I cannot install the package [FONT=courier new]update-notifier-common[/FONT] beacuse of broken dependency:

```

# apt install update-notifier-common
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 update-notifier-common : Depends: update-manager-core (>= 1:0.196.23) but 1:0.196.11 is to be installed
E: Unable to correct problems, you have held broken packages.

```
The to-be-installed version 0.154.1ubuntu9 is from Trusty ESM repo:
```

# apt-cache policy update-notifier-common
update-notifier-common:
  Installed: (none)
  Candidate: 0.154.1ubuntu9
  Version table:
     0.154.1ubuntu9 0
        500 [https://esm.ubuntu.com/ubuntu/](https://esm.ubuntu.com/ubuntu/) trusty-infra-security/main amd64 Packages
     0.154.1 0
        500 [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages

```

Bute there is no higher version of [FONT=courier new]update-manager-core[/FONT] than the installed version 0.196.11 form the trusty/main repo:
```

# apt-cache policy update-manager-core
update-manager-core:
  Installed: 1:0.196.11
  Candidate: 1:0.196.11
  Version table:
 *** 1:0.196.11 0
        500 [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
        100 /var/lib/dpkg/status

```

Is this a bug? What can I do to solve this?

---

### Post by ubfan1 on 2021-10-22
You seem to be missing several repos. in sources.list:
trusty-updates main restricted universe multiverse
and in the [FONT=courier new]ubuntu-esm-infra-trusty.list file
trusty-infra-updates main
I did the standard ESM on my 14.04 and that's was I got.  I don't do unattended updates however, so might not help your problem.
[/FONT]

---

