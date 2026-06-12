---
title: "Ubuntu 12.04 Update Manager not seeing my internet connection?"
date: 2013-04-27
forum: Installation &amp; Upgrades
---

### Post by cyb3rparadox on 2013-04-27
I am currently running Ubuntu 12.04 and when I try to update, I get the following error:
[ATTACH=CONFIG]241861[/ATTACH]

This is what is listed in the details:
```
W:Failed to fetch http://ppa.launchpad.net/jonabeck/ppa/ubuntu/dists/precise/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/jonabeck/ppa/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

I get basically the same error when I run sudo apt-get update from the terminal.

Could it be an issue with the URL for these two repos? I just performed an update that was successful but I'm still on 12.04 and am trying to upgrade to the latest version.

Thanks.

---

### Post by Bashing-om on 2013-04-27
cyb3rparadox; Hi !

I do not see any recent activity for this ppa, last listed supported version is "karmic";
>  [http://ppa.launchpad.net/jonabeck](http://ppa.launchpad.net/jonabeck)

Suggest that you disable these PPAs in your Software sources, and "update/upgrade" again.[INDENT=2]
just try'n to help

[/INDENT]

---

### Post by cyb3rparadox on 2013-04-29
Thanks, that did the trick.

---

