---
title: "apt repository broken when having only jammy and jammy-security apt-repos enabled"
date: 2023-03-01
forum: Installation &amp; Upgrades
---

### Post by daku8938 on 2023-03-01
[COLOR=#333333][FONT=monospace]Having installed Ubuntu 22 server from server-live-cd [https://releases.ubuntu.com/22.04/ubuntu-22.04.1-live-server-amd64.iso](https://releases.ubuntu.com/22.04/ubuntu-22.04.1-live-server-amd64.iso)
(md5sum e8d2a77c51b599c10651608a5d8c286f)[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]without network connection to internet (so no connection to ubuntu apt repositories). After offline installation completed, we remove the "jammy-updates" from the /etc/apt/sources.list so it looks like so:[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]# cat /etc/apt/sources.list
[/FONT][/COLOR]```
[COLOR=#333333][FONT=monospace]
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) jammy main restricted universe multiverse
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) jammy-security main restricted universe multiverse[/FONT][/COLOR]

```

[COLOR=#333333][FONT=monospace]Now we give the host network access and do "apt update" to refresh the apt repository.[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]We assume that the installed package libldap-2.5-0 version 2.5.12+dfsg-0ubuntu0.22.04.1
was installed from the ubuntu installer cd which is a version from jammy-updates.[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Now we are unable to install package "ldap-utils" because that depends on package libldap-2.5-0 version 2.5.11+dfsg-1~exp1ubuntu3.1 (which is older than the offline installed version 2.5.12+dfsg-0ubuntu0.22.04.1)
[/FONT][/COLOR]```

[COLOR=#333333][FONT=monospace]# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 22.04.1 LTS
Release: 22.04
Codename: jammy
[/FONT][/COLOR]
```
```

[COLOR=#333333][FONT=monospace]# apt-cache policy libldap-2.5-0
libldap-2.5-0:
  Installed: 2.5.12+dfsg-0ubuntu0.22.04.1
  Candidate: 2.5.12+dfsg-0ubuntu0.22.04.1
  Version table:
 *** 2.5.12+dfsg-0ubuntu0.22.04.1 100
        100 /var/lib/dpkg/status
     2.5.11+dfsg-1~exp1ubuntu3.1 500
        500 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) jammy-security/main amd64 Packages
     2.5.11+dfsg-1~exp1ubuntu3 500
        500 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) jammy/main amd64 Packages
[/FONT][/COLOR]
```
```

[COLOR=#333333][FONT=monospace]# apt install --simulate ldap-utils
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:
The following packages have unmet dependencies:
 ldap-utils : Depends: libldap-2.5-0 (= 2.5.11+dfsg-1~exp1ubuntu3.1) but 2.5.12+dfsg-0ubuntu0.22.04.1 is to be installed
E: Unable to correct problems, you have held broken packages.
[/FONT][/COLOR]
```
[COLOR=#333333][FONT=monospace]The problem is solved when adding line[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) jammy-updates main restricted universe multiverse[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]to /etc/apt/sources.list[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]But we want _only_ security updates, to keep the updates minimal.[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Other workaround is "apt remove libldap-2.5-0", then when installing ldap-utils that fetches the older libldap-2.5-0 version 2.5.11+dfsg-1~exp1ubuntu3.1 and repo is consistent.[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Questions:
- Can you confirm that the package version from the server-live-cd see above is the version from the jammy-updates repository?
- Do you agree that when the above question is answered yes, having jammy-updates apt-repository is mandatory?
- if jammy-updates repo should be mandatory should this be documented?

[/FONT][/COLOR]
This bug reported in Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/openldap/+bug/2008465](https://bugs.launchpad.net/ubuntu/+source/openldap/+bug/2008465)

---

### Post by ian-weisser on 2023-03-01
Looks like you merely chose the wrong version to install.

You picked 22.04.1, which includes nine months of -updates. As you have discovered, those updates must be reverted.
You should have used the original 22.04, which includes nothing from -updates.

---

### Post by daku8938 on 2023-03-02
Thanks Ian for your input. I wrote more in the launchpad bug.

---

