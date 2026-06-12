---
title: "Karmic Koala Alpha 6 Released..almost! Please Read!"
date: 2009-09-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by 23meg on 2009-09-17
Now that the release of Alpha 6, the last milestone release before the beta, is imminent, and the number of new testers is increasing, this is a good time to remember some basics regarding testing:

[list][*] The milestone releases (alphas, the beta and the RC) are snapshots of the package archive at their predecided release dates. **If you have the latest updates installed on your testing installation, you don't have to remove your current testing installation and install Alpha 6**, unless you want to test installation-specific components (the installer, bootloader etc.), or your installation is affected by potential corner cases that may arise during the development cycle that require a reinstall to fix. 


[*] Please wait for the official release announcement that will be posted to the [ubuntu-devel-announce mailing list]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce"), regardless of whether the images seem to be downloadable at URLs posted around forums, blogs or IRC. They may be incomplete, and downloading before the announcement can slow down the syncing of the mirrors and delay the release. If you're not subscribed to the mailing list, you can check for the announcement [here]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-September/date.html").


[*] If you're just starting to test Karmic, please take a look at [this wiki page]("https://wiki.ubuntu.com/UbuntuDevelopment/UsingDevelopmentReleases") for information on various testing methods and good practices.


[*] Once you've started testing, **do not upgrade your installation blindly** - in special, avoid partial upgrades offered by Update Manager unless you know precisely why it's offering a partial upgrade. Regardless of which tool (APT, Update Manager, Synaptic, Aptitude) you're using to upgrade your packages, **always check the list of packages to be removed, upgraded and installed before each upgrade**. If in doubt, check the changelogs ("Package > Download Changelog" in Synaptic, or "aptitude changelog package_name", or at [packages.ubuntu.com]("http://packages.ubuntu.com")) to see why a package may be being removed.


[*] If you run into problems, you're most likely not alone; do a bug search at the bug tracker and/or a forum search in this forum before starting new threads.[/list]

---

### Post by VMC on 2009-09-17
Thanks for this information. I wasn't aware of the wiki page. Good information there as well. I'm interested if that "changes" section and would it help me or not. I'm not a member and read a few of the comments. That might be more reading than I care to take on.

I think the Active Status Page would be more beneficial for me.

---

### Post by knarf on 2009-09-17
May I add to this that it is always a good idea to check the forum and/or the mailing lists before doing an update? If one of the updated packages causes trouble you'll probably find out that way before doing the update yourself. You can either decide to wait with the update, or update with the intention of fixing the børkage...

---

### Post by sena_akada on 2009-09-17
after the nvidia incident, i will wait for beta :P

---

### Post by psyke83 on 2009-09-17
23meg,

Those guidelines are exactly what's needed (particularly regarding upgrades), thanks for posting them. Let's hope that more people pay attention in future!

---

