---
title: "Upgrade from 8.04"
date: 2010-07-09
forum: Installation &amp; Upgrades
---

### Post by asai on 2010-07-09
Hi,
I am upgrading a Hardy server to Lucid.
Used this command:
```
sudo do-release-upgrade --devel-release
```

Stops with this error:
```
Exception during pm.DoInstall():  E:Couldn't configure pre-depend jre for openoffice.org-writer2latex, probably a dependency cycle.
```

Any suggestions to fix this?

---

### Post by davidmohammed on 2010-07-09
dont use the extra flag if you want to goto lucid.

i.e.


sudo apt-get install update-manager-core

edit /etc/update-manager/release-upgrades and set Prompt=normal 

Launch the upgrade tool: 

sudo do-release-upgrade

Follow the on-screen instructions.

---

### Post by lechien73 on 2010-07-09
The problem can also be OpenOffice related. Others experienced the same problem upgrading from Jaunty to Karmic. You could try:

```
sudo apt-get remove openoffice.org-writer2latex
```

And then run the upgrade again. In fact some suggested that it was better to completely remove OpenOffice and then re-install after the upgrade.

---

### Post by asai on 2010-07-09
> **lechien73 said:**
> The problem can also be OpenOffice related. Others experienced the same problem upgrading from Jaunty to Karmic. You could try:

```
sudo apt-get remove openoffice.org-writer2latex
```

And then run the upgrade again. In fact some suggested that it was better to completely remove OpenOffice and then re-install after the upgrade.

Looks like this did the trick.
The update process is taking place now. I will update the thread when it is completed. :)

---

