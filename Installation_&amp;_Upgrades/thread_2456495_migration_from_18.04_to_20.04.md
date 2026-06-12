---
title: "migration from 18.04 to 20.04"
date: 2021-01-12
forum: Installation &amp; Upgrades
---

### Post by extraspecialbitter2 on 2021-01-12
I just received a computer from my workplace that is running Ubuntu 18.04 and would like to upgrade it to 20.04 to take advantage of some features not available in the former version. Am I naive to think that it should be just a matter of updating my /etc/apt/sources.list file to use "focal" instead of "bionic", and then running "sudo apt-get update && sudo apt-get dist-upgrade"?

---

### Post by TheFu on 2021-01-12
> **extraspecialbitter2 said:**
> I just received a computer from my workplace that is running Ubuntu 18.04 and would like to upgrade it to 20.04 to take advantage of some features not available in the former version. Am I naive to think that it should be just a matter of updating my /etc/apt/sources.list file to use "focal" instead of "bionic", and then running "sudo apt-get update && sudo apt-get dist-upgrade"?

That is the debian way, but not the ubuntu way.
Search these formus for detailed steps. I don't want to type answers over again, perhaps missing something important. Make a 100% backup as the first step. Sometimes replacing a car engine fails. That is what an OS version upgrade is. If you can't put the old engine back and try over, what then?

---

### Post by extraspecialbitter2 on 2021-01-12
> **TheFu said:**
> That is the debian way, but not the ubuntu way.
Search these formus for detailed steps. I don't want to type answers over again, perhaps missing something important. Make a 100% backup as the first step. Sometimes replacing a car engine fails. That is what an OS version upgrade is. If you can't put the old engine back and try over, what then?

Thanks for the reply. I did do a search for "18.04 to 20.4 migration" but saw no matches. Perhaps others can point me to existing threads, which I would be happy to peruse.

I do have the Ubuntu 20.4 distribution on a USB thumb drive and could just do a clean install. I've already backed up any data I'd want to keep in the event that I go that route.

---

### Post by grahammechanical on 2021-01-12
This is the official explanation. It is comprehensive and may be too much information for someone who is unfamiliar with upgrading from one Ubuntu LTS version to another.

[https://ubuntu.com/blog/how-to-upgrade-from-ubuntu-18-04-lts-to-20-04-lts-today](https://ubuntu.com/blog/how-to-upgrade-from-ubuntu-18-04-lts-to-20-04-lts-today)

One thing you can do which is simple is to load Software & Updates>Updates tab. Make sure that the panel Notify me of a new Ubuntu version is set to For Long-term Support Versions.

While you are in Software & Updates open the Other Software tab and disable any PPA that might be there. Then run Software Updater. You may get a dialog box inviting you to upgrade.

Has there been any user customizations to the User Interface? Revert them to default.

Regards

---

### Post by extraspecialbitter2 on 2021-01-12
> **grahammechanical said:**
> This is the official explanation. It is comprehensive and may be too much information for someone who is unfamiliar with upgrading from one Ubuntu LTS version to another.

[https://ubuntu.com/blog/how-to-upgrade-from-ubuntu-18-04-lts-to-20-04-lts-today](https://ubuntu.com/blog/how-to-upgrade-from-ubuntu-18-04-lts-to-20-04-lts-today)

One thing you can do which is simple is to load Software & Updates>Updates tab. Make sure that the panel Notify me of a new Ubuntu version is set to For Long-term Support Versions.

While you are in Software & Updates open the Other Software tab and disable any PPA that might be there. Then run Software Updater. You may get a dialog box inviting you to upgrade.

Has there been any user customizations to the User Interface? Revert them to default.

Regards

Thank you for the reply. I've only had this computer for a few days, so I'd rather go ahead and perform an upgrade now versus later.

---

### Post by extraspecialbitter2 on 2021-01-13
> **grahammechanical said:**
> This is the official explanation. It is comprehensive and may be too much information for someone who is unfamiliar with upgrading from one Ubuntu LTS version to another.

[https://ubuntu.com/blog/how-to-upgrade-from-ubuntu-18-04-lts-to-20-04-lts-today](https://ubuntu.com/blog/how-to-upgrade-from-ubuntu-18-04-lts-to-20-04-lts-today)

One thing you can do which is simple is to load Software & Updates>Updates tab. Make sure that the panel Notify me of a new Ubuntu version is set to For Long-term Support Versions.

While you are in Software & Updates open the Other Software tab and disable any PPA that might be there. Then run Software Updater. You may get a dialog box inviting you to upgrade.

Has there been any user customizations to the User Interface? Revert them to default.

Regards

I followed the instructions to migrate from 18.04 to 20.04 using the graphical installer, and it was fairly smooth with the exception of a delay introduced by Adobe's retirement of Flash, documented at [https://ubuntuforums.org/showthread.php?t=2452516&highlight=flashplayer](https://ubuntuforums.org/showthread.php?t=2452516&highlight=flashplayer). Once that step timed out, the migration continued through the reboot.

I noticed that /etc/lsb-release still looks like this:

```
pmena@pmena-7080=> cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=18.04
DISTRIB_CODENAME=bionic
DISTRIB_DESCRIPTION="Ubuntu 18.04.2 LTS (beaver-osp1-ygritte X40)"

```

/etc/os-release, however, looks like this:

```
pmena@pmena-7080=> cat /etc/os-release NAME="Ubuntu"
VERSION="20.04.1 LTS (Focal Fossa)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 20.04.1 LTS"
VERSION_ID="20.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=focal
UBUNTU_CODENAME=focal

```

I'm hoping this is a leftover from the upgrade, but it's rather confusing.

---

### Post by TheFu on 2021-01-13
**lsb_release -a** is the ubuntu way.

Ubuntu isn't debian.

---

### Post by extraspecialbitter2 on 2021-01-13
> **TheFu said:**
> **lsb_release -a** is the ubuntu way.

Ubuntu isn't debian.

Good to know.

```
pmena@pmena-7080=> lsb_release -aNo LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 20.04.1 LTS
Release:	20.04
Codename:	focal

```

---

### Post by TheFu on 2021-01-13
use **sudo apt full-upgrade** to go from 20.04.1 --> 20.04.2 --> 20.04.3 ... 
use **sudo do-release-upgrade**  to go from 18.04.x to 20.04.x, but only after doing a full backup and being 100% patched with a update+full-upgrade apt cycle first. Usually best to remove any PPAs and manually installed .deb files too.  Manually installed .deb files often break the Canonical repos and will hold back package upgrades. Usually it takes a few to 6 months before the problems start.  Definitely keep a list of any manually installed .deb files, so you can remove them when the dependencies break.

---

### Post by extraspecialbitter2 on 2021-01-13
> **TheFu said:**
> use **sudo apt full-upgrade** to go from 20.04.1 --> 20.04.2 --> 20.04.3 ... 
use **sudo do-release-upgrade**  to go from 18.04.x to 20.04.x, but only after doing a full backup and being 100% patched with a update+full-upgrade apt cycle first. Usually best to remove any PPAs and manually installed .deb files too.  Manually installed .deb files often break the Canonical repos and will hold back package upgrades. Usually it takes a few to 6 months before the problems start.  Definitely keep a list of any manually installed .deb files, so you can remove them when the dependencies break.

Thanks for the tip. Being old-school, I do prefer the command line over the graphical installer.

---

### Post by astronomertom on 2021-04-05
> **TheFu said:**
> use **sudo apt full-upgrade** to go from 20.04.1 --> 20.04.2 --> 20.04.3 ... 
use **sudo do-release-upgrade**  to go from 18.04.x to 20.04.x, but only after doing a full backup and being 100% patched with a update+full-upgrade apt cycle first. Usually best to remove any PPAs and manually installed .deb files too.  Manually installed .deb files often break the Canonical repos and will hold back package upgrades. Usually it takes a few to 6 months before the problems start.  Definitely keep a list of any manually installed .deb files, so you can remove them when the dependencies break.

Is there any way to identify the problem packages if you don't have a list of all the Debian installations?  Perhaps using 
**apt list --installed**
or similar?
Could packages with dependencies built from source also contribute to the problem?

I would much prefer an upgrade over a clean install but have been unable to do the update since the GRUB 2 problems from last year.  

When I try
**sudo do-release-upgrade**
I still get the 
"Failed to connect to [https://changelogs.ubuntu.com/meta-release-lts](https://changelogs.ubuntu.com/meta-release-lts). Check your Internet connection or proxy settings"
which still makes no sense.

I've been following the threads here for months on this topic.  Tried many of the suggestions (disable PPAs, etc.) with no progress.

Removing the Debian packages is the one item that would be a huge effort if I just uninstalled everything.  At present, I can still at least *use* this machine at 18.04, but getting it back to a usable configuration after a clean install may keep it unusable for a week or more tracking down all the custom packages and configurations.

Is there anything else that I can check?

Thanks,
Tom

---

