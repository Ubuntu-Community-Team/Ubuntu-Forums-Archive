---
title: "Upgrading to Gutsy Gibbon from Feisty Fawn"
date: 2007-07-27
forum: Installation &amp; Upgrades
---

### Post by bostoys on 2007-07-27
Hi all,

I've been reading a lot about different ways to upgrade to gutsy tribe 3 from feisty. however, when I run update-manager -c -d or update manager -c or update-manager -d, nothing happens. i mean, the update manager comes up but it says that it's up to date, and i'm positive i'm only on 7.04. why wouldn't it update? 
what other ways are there to update?
thanks.

---

### Post by rovernaut on 2007-07-27
> **bostoys said:**
> Hi all,

I've been reading a lot about different ways to upgrade to gutsy tribe 3 from feisty. however, when I run update-manager -c -d or update manager -c or update-manager -d, nothing happens. i mean, the update manager comes up but it says that it's up to date, and i'm positive i'm only on 7.04. why wouldn't it update? 
what other ways are there to update?
thanks.
I am only a newbie, but I think since you have installed feisty  and all entries in the repositories are reference to feisty then when you ask for an upgrade. The system searches for updates in the repos and says their up to date.
As Gutsy hasn't been released yet and is still in testing builds there is no option in the repos to upgrade to it
If the repos were altered with information relating to  gusty  with the server details then you might be able to upgrade.
 As I said I'm only a newbie

---

### Post by Seisen on 2007-07-27
Try this

```
sudo sed -e 's/\sfeisty/ gutsy/g' -i /etc/apt/sources.list
sudo apt-get update
sudo apt-get dist-upgrade
```

---

