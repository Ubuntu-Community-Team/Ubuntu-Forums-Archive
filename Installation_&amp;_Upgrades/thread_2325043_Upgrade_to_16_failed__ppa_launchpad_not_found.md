---
title: "Upgrade to 16 failed  ppa launchpad not found"
date: 2016-05-18
forum: Installation &amp; Upgrades
---

### Post by l6griffin on 2016-05-18
I'm trying to upgrade 15.10 on my laptop to 16.04 LTS and it fails with these errors;       
Failed to fetch [http://ppa.launchpad.net/ubuntu-nexus7/ubuntu-nexus7-installer/ubuntu/dists/wily/main/binary-amd64/Packages](http://ppa.launchpad.net/ubuntu-nexus7/ubuntu-nexus7-installer/ubuntu/dists/wily/main/binary-amd64/Packages)  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/ubuntu-nexus7/ubuntu-nexus7-installer/ubuntu/dists/wily/main/binary-i386/Packages](http://ppa.launchpad.net/ubuntu-nexus7/ubuntu-nexus7-installer/ubuntu/dists/wily/main/binary-i386/Packages)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.

I ran, apt-get update, and tried again to update same problem.
I then ran, apt-get remove launchpad, not there so I installed it, same errors.

Not sure where to go from here.

---

### Post by Bashing-om on 2016-05-18
l6griffin; Hello;

When you look:
[http://ppa.launchpad.net/ubuntu-nexus7/ubuntu-nexus7-installer/ubuntu/dists/](http://ppa.launchpad.net/ubuntu-nexus7/ubuntu-nexus7-installer/ubuntu/dists/)
You see that raring (13.04) was the last release supported.

Disable these PPAs .. 
Now what results:
```

sudo apt update
sudo apt full-upgrade

```

Always the better practice to remain within our software repository as else

[INDENT][INDENT]things change
[/INDENT][/INDENT]

---

### Post by l6griffin on 2016-05-18
That solved it. That ppa may have been installed with the launchpad plugin for Firefox.

Thank you

---

### Post by Bashing-om on 2016-05-18
l6griffin; :)

Glad to help.

[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT]

---

