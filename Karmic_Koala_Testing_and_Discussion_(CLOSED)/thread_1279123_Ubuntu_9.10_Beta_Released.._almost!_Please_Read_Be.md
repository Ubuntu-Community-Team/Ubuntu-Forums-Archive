---
title: "Ubuntu 9.10 Beta Released.. almost! Please Read Before Testing!"
date: 2009-09-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by 23meg on 2009-09-30
The release of Ubuntu 9.10 Beta, the last milestone release before the Release Candidate for Ubuntu 9.10, is imminent. Since we expect many new testers to pick up testing with this milestone, this is a good time to remember some basics regarding testing:

[list][*] The milestone releases (alphas, the beta and the RC) are snapshots of the package archive at their predecided release dates. **If you have the latest updates installed on your testing installation, you don't have to remove your current testing installation and install the beta**, unless you want to test installation-specific components (the installer, bootloader etc.), or your installation is affected by potential corner cases that may arise during the development cycle that require a reinstall to fix. 


[*] Please wait for the official release announcement that will be posted to the [ubuntu-devel-announce mailing list]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce"), regardless of whether the images seem to be downloadable at URLs posted around forums, blogs or IRC. They may be incomplete, and downloading before the announcement can slow down the syncing of the mirrors and delay the release. If you're not subscribed to the mailing list, you can check for the announcement [here]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-September/date.html").


[*] If you're just starting to test Karmic, please take a look at [this wiki page]("https://wiki.ubuntu.com/UbuntuDevelopment/UsingDevelopmentReleases") for information on various testing methods and good practices.


[*] Once you've started testing, do not upgrade your installation blindly - especially, avoid partial upgrades offered by Update Manager unless you know precisely why it's offering a partial upgrade. Regardless of which tool (APT, Update Manager, Synaptic, Aptitude) you're using to upgrade your packages, always check the list of packages to be removed, upgraded and installed before each upgrade. If in doubt, check the changelogs ("Package > Download Changelog" in Synaptic, or "aptitude changelog package_name", or at [packages.ubuntu.com]("http://packages.ubuntu.com")) to see why a package may be being removed.

[*] When you install the beta, and just keep upgrading your packages until the final release, you'll have the final release; you don't have to reinstall it. But you may want to, in case you're affected by potential unforeseen corner cases that may require a reinstall to fix.


[*] If you run into problems, you're most likely not alone; please do a bug search at [the bug tracker]("https://bugs.launchpad.net/ubuntu") and/or a forum search in this forum (note the "Search this Forum" item on the upper right corner in the thread index) before starting new threads.


[*] [To report a bug]("https://help.ubuntu.com/community/ReportingBugs") in the default desktop applications, use the "Help > Report a Problem" menu item. Where this is not applicable, use the "ubuntu-bug" command line bug reporting tool. You can invoke it by pressing Alt+F2 to open the "Run Application" window, or starting a terminal emulator, and typing ```
ubuntu-bug package_name
``` and pressing "Enter", where *package_name* is the name of the package you want to report a bug in.

If you have trouble finding the right package to report the bug in, take a look at the [Bugs/FindRightPackage]("https://wiki.ubuntu.com/Bugs/FindRightPackage") page on the wiki. If that doesn't help, feel free to start a thread to ask for assistance.

[/list]

---

