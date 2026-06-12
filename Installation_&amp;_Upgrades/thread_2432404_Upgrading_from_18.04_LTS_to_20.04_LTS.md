---
title: "Upgrading from 18.04 LTS to 20.04 LTS"
date: 2019-12-02
forum: Installation &amp; Upgrades
---

### Post by frank.datank on 2019-12-02
Is it possible to upgrade from 18.04 LTS straight to 20.04 LTS? If so how would one accomplish this? Thanks and sorry if this has already been asked, I searched and could not find anything on google.

---

### Post by Impavidus on 2019-12-02
Not yet. Ubuntu 20.04 will be released in April 2020 and the upgrade will be offered late July or early August. If you tell the update manager to prompt for upgrades to LTS releases, the upgrade will be offered then.

Ubuntu 20.04 is still in development. If you really wish, you can try to upgrade using the command line:```
sudo do-release-upgrade -d
```But this is only for those who want to hunt bugs. Don't try it on a production system.

---

### Post by CatKiller on 2019-12-02
Impavidus has already covered the fact that the version numbers are date based, so you can't do so yet.

For the mechanics of it, when the time comes, purging any PPAs that you've been using, and reinstalling the -desktop metapackage for your flavour if you've removed that for any reason, prior to doing the upgrade, will give you the best chance of going through the upgrade process without any package conflicts.

---

### Post by rsteinmetz70112 on 2019-12-02
Doing an upgrade to an LTS version is covered in the previous posts. Set the update manager to offer only LTS upgrades, it will prompt you when it becomes availibel. The LTS upgrade is not usually offered until the .1 release so any hiccups can be addressed. That is usually June or July.
Before stating the upgrade make sure your 18.04 is fully updated and your sources cleaned up.

```
sudo apt update
sudo apt full-upgrade
do-release-upgrade
```

Fun fact*** do-release-upgrade*** does not require a sudo, it will download some stuff then prompt for authorization, the sudo doesn't hurt though.

---

### Post by frank.datank on 2019-12-03
I usually do fresh installs of OSs once every 1 to 2 years, so a 2 year cycle is not bad. I will probably fresh install next time. I just wanted to know if it was possible, so thanks for the replies.

---

