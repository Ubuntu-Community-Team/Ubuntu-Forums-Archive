---
title: "Failed to Fetch."
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by bugz0r on 2006-10-26
[http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg](http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg)

When I try to upgrade, it fails to fetch this ^. Help.

---

### Post by rmjb on 2006-10-26
That's for a 3rd party (non-ubuntu) repository. It looks like the site is currently down... probably from all the strain of people updating. Where ever you added this repository from, whatever howto or other installation suite (like Automatix or EasyUbuntu) guided you to it, you should probably notify them.

- rmjb

---

### Post by phrawzty on 2006-10-26
> **rmjb said:**
> Where ever you added this repository from, whatever howto or other installation suite (like Automatix or EasyUbuntu) guided you to it, you should probably notify them.

I got the same error while updating as well, and i'd hazard a guess that i received it from the same process:

```
$ gksu "update-manager -c"
```

As indicated by the help.ubuntu Edgy Upgrade page:
[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

:(

---

### Post by rmjb on 2006-10-26
You can ignore this error during the upgrade process since it's for a third party repository... you'll need to change it for edgy in any case.

To not get the error, open up your /etc/apt/sources.list file as root:

gksu gedit /etc/apt/sources.list

and comment out the lines that refer to [http://packages.freecontrib.org](http://packages.freecontrib.org)...

You can comment it out by putting a # at the beginning of the line.

Any packages you had installed from the 3rd party repository may not work until you get them upgraded, from the edgy version of the repository.

But it seems that particular one is down right now.

- rmjb

---

