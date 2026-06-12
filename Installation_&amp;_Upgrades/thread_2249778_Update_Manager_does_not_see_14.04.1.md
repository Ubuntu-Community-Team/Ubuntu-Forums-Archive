---
title: "Update Manager does not see 14.04.1"
date: 2014-10-24
forum: Installation &amp; Upgrades
---

### Post by hhall on 2014-10-24
Hi all.

This may have been asked before. I am using the previous LTS, and as I was travelling all summer and had little chance of making backups and so on, I am only now finding the time to update to 14.014.1 LTS. Now, the update manager does not actually mention it or give the option. It is set to alert me to new LTS versions, and I have tried several source servers, including the one nearest to me, and the main one. Does anyone have an idea? Thanks, HH

---

### Post by grahammechanical on 2014-10-24
Updating to a point release of an LTS release is not done in the same way as upgrading from one release to the next one. Have you updated the system recently? Then run

```
lsb_release -a
```

and see what it says. We update to a point release by the usual method of updating the system.

Regards.

---

### Post by hhall on 2014-10-24
Hi Graham.

Can you explain the -a? I just want to know why I am doing what I am doing. Should the Update Manager not show the new release, as in, is that normal?

Thanks,

Heinrich

---

### Post by Vladlenin5000 on 2014-10-24
You can always do *man <command> *to get all the available documented info for <command> including switches/parameters.
In this case ```
man lsb_release
``` will show that -a posts all the information.

Again, updating to a point release is done by regular updates therefore update manager will NOT specifically show that as a new release (and it isn't). Here's mine as an example: ```
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:core-4.1-amd64:core-4.1-noarch:security-4.0-amd64:security-4.0-noarch:security-4.1-amd64:security-4.1-noarch
Distributor ID:    Ubuntu
Description:    [COLOR=#008000]Ubuntu 14.04.1 LTS[/COLOR]
Release:    14.04
Codename:    trusty
```

---

