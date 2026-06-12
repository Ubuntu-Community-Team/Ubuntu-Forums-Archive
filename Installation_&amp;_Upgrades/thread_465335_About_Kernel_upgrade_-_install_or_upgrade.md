---
title: "About Kernel upgrade - install or upgrade?"
date: 2007-06-05
forum: Installation &amp; Upgrades
---

### Post by neel on 2007-06-05
Hi,

I am fairly new to Ubuntu and have been reading the forums/mailing-lists a lot about package updates/upgrades/dist-upgrades. Most of it makes sense to me, except the following about kernel upgrades (while staying within a release, say Edgy):

* doing a usual `sudo aptitude update` followed by `sudo aptitude upgrade`, upgrades the kernel as well, leaving you no option to go back in case of a problem. Shouldn't we be 'installing' the new kernel instead, so we can always boot into the older version?

I am moving over from the RedHat world and it just makes more sense to install the new kernel instead of upgrading it, as is the case in RH. I remember you could tell the nightly yum to handle the kernel packages differently. Is there an easier way to tell aptitude to install the kernel packages during the upgrade process, than saying `sudo aptitude install linux-image-<version>` before the `sudo aptitude upgrade` ? At the least, is there a way to avoid having to enter the <version> each time?

And then there is the dist-upgrade...
* the man page and documentation advice to use aptitude dist-upgrade with caution. But it seems to be the only way to get a new kernel when the kernel package's name has been changed (say, from linux-image-2.6.17-10-generic to linux-image-2.6.17-11-generic). Correct me if I am wrong, but when a name change happens, a usual `sudo aptitude update` followed by `sudo aptitude upgrade` does not upgrade the kernel. So, that means I have to take note of a name change and then go for a dist-upgrade instead, right?

I think there should be (and probably there is) a simpler mechanism. Please point me in the right direction... And no, the curses-based interface to aptitude is not a scalable solution when you have tens/hundreds of boxes to upgrade.

Thanks.

-Neel

---

### Post by luisromangz on 2007-06-05
I think that the actual behavior in Ubuntu is that the kernel metapackage for your architecture is uptated, and its dependencies became the new kernel packages, so in fact you have various kernels installed so you can use the old one if the newer gives you problems.

And I don't think it is necessary to perform a dist-upgrade to get a new kernel update.

Bye!

---

### Post by neel on 2007-06-05
luisromangz,

What you say is not quite what I observe. Here's precisely what is happening:

- installed 6.10 Edgy server from alternate-i386.iso CD, which comes with linux-image-2.6.17-10-generic v2.6.17-10.33 by default
- did sudo aptitude update, followed by sudo aptitude upgrade, which:
[INDENT]- kept back linux-image-generic
- and upgraded linux-image-2.6.17-10-generic to v2.6.17.1-10.34[/INDENT]
- and as a result there was only one kernel image on the system, i.e., v2.6.17.1-10.34

Besides, in the repository the latest kernel is linux-image-2.6.17-11-generic v2.6.17.1-11.38, which is not installed via the usual upgrade. I have to either explicitly say `sudo aptitude install linux-image-2.6.17-11-generic` or do a `sudo aptitude dist-upgrade` to install this kernel and also upgrade the package linux-image-generic.

Is this the right behavior? Am I missing something fundamental?

Thanks.

-Neel

---

