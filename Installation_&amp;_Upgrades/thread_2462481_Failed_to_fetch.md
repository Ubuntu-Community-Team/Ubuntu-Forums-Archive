---
title: "Failed to fetch"
date: 2021-05-21
forum: Installation &amp; Upgrades
---

### Post by Otto-C on 2021-05-21
Doing command line update and got this.
How to move forward?

Reading package lists... Done                     
E: Failed to fetch [https://deb.etcher.io/dists/stable/InRelease](https://deb.etcher.io/dists/stable/InRelease)  403  Forbidden [IP: 34.218.153.129 443]
E: The repository 'https://deb.etcher.io stable InRelease' is no longer signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.


tia
otto

---

### Post by Dennis N on 2021-05-21
You could disable the repository for Etcher and rerun the update.

---

### Post by garvinrick4 on 2021-05-21
> sudo gedit /etc/apt/sources.list
Go to offending deb.etcher.io and put a # in front of line and hit save.
It is called commenting out a line and will not use line while # is in front of line.

---

### Post by ActionParsnip on 2021-05-22
[https://github.com/balena-io/etcher/issues/3084](https://github.com/balena-io/etcher/issues/3084)

Considering that there are plenty of other apps to transfer ISO files to USB / SDCards, I'd just use something else if this goes on for a while.

---

