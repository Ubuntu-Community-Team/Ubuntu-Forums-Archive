---
title: "Cannot upgrade ubuntu-desktop?"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by Craga_89 on 2006-10-26
Nothing that urgent! It's just that I've been using Edgy Eft RC1 for about a month now (Or however long its been out!) and I must say I've been very pleased with its overall performance and stability, a very good Candidate Release imo. However, over the past few weeks I've noticed something odd about the Update manager.

When I first got RC1, whenever I used the update manager it said "Not all updates can be installed, you will need to perform a distribution upgrade" or something similar to that and gave me a choice as to whether or not to proceed with the dist upgrade. For the first few weeks it performed flawlessly, upgrading my distro nearly everyday (very impressed with btw!), but in the weeks nearing the final release it seems to be having ap roblem upgrading.

Whenever I try to distribution upgrade with the manager or even apt-get, it fails on the ubuntu-desktop package reading this message on the console:

```

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-desktop: Depends: xorg but it is not going to be installed
E: Broken packages

```

I do see the broken packages error, but what seems strange is that I **do** have Xorg 7.1 installed in accordance to the edgy packages, maybe ubuntu-desktop is referring to another version which can't be installed with the one current installed? I don't know... Any ideas would be appreciated.

Thanks in advance, Craig.

---

### Post by neymac on 2006-10-27
I have the same problem here after upgrade Dapper to Edgy.
xorg is not installed
ubuntu-desktop is not installed

When I login XGL session everything works but update nor upgrade.
At gnome session I can`t upgrade either.

---

