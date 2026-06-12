---
title: "Ubuntu 9.10 RC Released - Please Read Before Testing"
date: 2009-10-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by 23meg on 2009-10-22
The Release Candidate for Ubuntu 9.10, which is the last milestone release before the final release, [has been released]("https://lists.ubuntu.com/archives/ubuntu-announce/2009-October/000126.html"). The Release Candidate is a production-quality pre-release which would ideally be functionally identical to the final release.

Since we expect the largest amount of testers by this milestone, this is a good time to remember some testing basics:

[list] [*] The milestone releases (alphas, the beta and the Release Candidate) are snapshots of the package archive at their predecided release dates. **If you have the latest updates installed on your testing installation, you don't have to remove your current testing installation and install the Release Candidate**, unless you want to test installation-specific components (the installer, bootloader etc.), or your installation is affected by potential corner cases which may arise during the development cycle that may require a fresh install to fix. 


[*] If you're just starting to test Karmic, please take a look at [this wiki page]("https://wiki.ubuntu.com/UbuntuDevelopment/UsingDevelopmentReleases") for information on various testing methods and good practices.


[*] Once you've started testing, do not upgrade your installation blindly - **especially, avoid partial upgrades offered by Update Manager unless you know precisely why it's offering a partial upgrade**. Regardless of which tool (APT, Update Manager, Synaptic, Aptitude) you're using to upgrade your packages, always check the list of packages to be removed, upgraded and installed before each upgrade. If in doubt, check the changelogs ("Package > Download Changelog" in Synaptic, or "aptitude changelog package_name", or at [packages.ubuntu.com]("http://packages.ubuntu.com")) to see why a package may be being removed.

Refer to [this thread]("http://ubuntuforums.org/showthread.php?t=1286309") for further explanation of the "Partial Upgrade".


[*] When you install the Release Candidate, and just keep upgrading your packages until the final release, you'll have the final release; you don't have to install it from scratch. But you may want to, in the case that you may be affected by potential unforeseen corner cases that may require a fresh install to fix, and/or due to outdated user configuration files. It's also a good idea to do a fresh install if you've modified your testing installation (with custom configuration, libraries from outside the Ubuntu repositories, etc.) to the extent that you've lost grasp of its exact contents.


[*] The Release Candidate is still likely to have outstanding bugs. Please do a bug search at [the bug tracker]("https://bugs.launchpad.net/ubuntu") and/or a forum search in this forum (note the "Search this Forum" item on the upper right corner in the thread index) before starting new threads.

Note that since we're in the final phase of the development cycle, bug fixing focus will be restricted to high-impact showstopper bugs, and changes from this point on are only permitted at the discretion of the release manager.


[*] [To report a bug]("https://help.ubuntu.com/community/ReportingBugs") in the default desktop applications, use the "Help > Report a Problem" menu item. Where this is not applicable, use the "ubuntu-bug" command line bug reporting tool. You can invoke it by pressing Alt+F2 to open the "Run Application" window, or starting a terminal emulator, and typing ```
ubuntu-bug package_name
``` and pressing "Enter", where *package_name* is the name of the package you want to report a bug in.

If you have trouble finding the right package to report the bug in, take a look at the [Bugs/FindRightPackage]("https://wiki.ubuntu.com/Bugs/FindRightPackage") page on the wiki. If that doesn't help, feel free to start a thread to ask for assistance.

[/list]

---

