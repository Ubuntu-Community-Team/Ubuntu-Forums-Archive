---
title: "Ubuntu 9.10 Release Candidate - Please Read Before Testing"
date: 2009-10-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by 23meg on 2009-10-21
The Release Candidate for Ubuntu 9.10, which will be the last milestone release before the final release, is imminent. The Release Candidate is a production-quality pre-release which would ideally be functionally identical to the final release.

Since we expect more testers to pick up testing with this milestone, this is a good time to remember some testing basics:

[list][*] Please **do not attempt to download the Release Candidate before the official release announcement** that will be posted to the [ubuntu-announce mailing list]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-announce"), regardless of whether the technical overview page seems to be up, and the images seem to be downloadable at URLs posted around forums, blogs, IRC and news websites. They may be incomplete and broken, and downloading before the announcement can slow down the syncing of the mirrors and delay the release. If you're not subscribed to the mailing list, you can check for the announcement [here]("https://lists.ubuntu.com/archives/ubuntu-announce/2009-October/date.html").


[*] The milestone releases (alphas, the beta and the Release Candidate) are snapshots of the package archive at their predecided release dates. **If you have the latest updates installed on your testing installation, you don't have to remove your current testing installation and install the Release Candidate**, unless you want to test installation-specific components (the installer, bootloader etc.), or your installation is affected by potential corner cases which may arise during the development cycle that may require a fresh install to fix. 


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

### Post by linbetwin on 2009-10-22
Is the RC coming today ?

---

### Post by neglesaks on 2009-10-22
> **linbetwin said:**
> Is the RC coming today ?

Most likely. The development releases tend to be on schedule, but still released late in the evening (europe time). So give it a few more hours.

Oh, and please use bittorrent if you can? It helps out everyone...

---

### Post by viper8 on 2009-10-22
> **neglesaks said:**
> Most likely. The development releases tend to be on schedule, but still released late in the evening (europe time). So give it a few more hours.

Oh, and please use bittorrent if you can? It helps out everyone...

It has been released:
[http://www.ubuntugeek.com/ubuntu-9-10-karmic-rc-released.html](http://www.ubuntugeek.com/ubuntu-9-10-karmic-rc-released.html)

Torrents avail as well

---

### Post by neglesaks on 2009-10-22
> **viper8 said:**
> It has been released:
[http://www.ubuntugeek.com/ubuntu-9-10-karmic-rc-released.html](http://www.ubuntugeek.com/ubuntu-9-10-karmic-rc-released.html)

Torrents avail as well

The Ubuntu Release blog disagrees, and that is usually right on the heels of the ubuntu-release mailing list.

[http://release-blog.ubuntu.com/](http://release-blog.ubuntu.com/)

In any case, please hold your horses until 23meg OK's it by posting a RC release topic here on the forums. Standard warnings apply.

(edit: the official 9.10rc page disagrees as well: [http://www.ubuntu.com/testing/910rc](http://www.ubuntu.com/testing/910rc) )

---

### Post by viper8 on 2009-10-22
> **neglesaks said:**
> The Ubuntu Release blog disagrees, and that is usually right on the heels of the ubuntu-release mailing list.

[http://release-blog.ubuntu.com/](http://release-blog.ubuntu.com/)

In any case, please hold your horses until 23meg OK's it by posting a RC release topic here on the forums. Standard warnings apply.

(edit: the official 9.10rc page disagrees as well: [http://www.ubuntu.com/testing/910rc](http://www.ubuntu.com/testing/910rc) )

That's cool...I agree 100%, no rush :) 

I did notice that on the top of [http://releases.ubuntu.com/releases/9.10/](http://releases.ubuntu.com/releases/9.10/), it shows "Ubuntu 9.10 (Karmic Koala) Release Candidate", but better off to wait for some official word.

ETA:  Ohhh but some of the isos are from 10/20....you're probably right!

---

### Post by jatinps on 2009-10-22
a few more hours to go - but i am running karmic beta, so I guess with the daily updates I must already be running the release candidate :)

---

### Post by neglesaks on 2009-10-22
> **jatinps said:**
> a few more hours to go - but i am running karmic beta, so I guess with the daily updates I must already be running the release candidate :)

Essentially, yes you are.

---

### Post by linbetwin on 2009-10-22
Here it is:
[http://www.ubuntugeek.com/ubuntu-9-10-karmic-rc-released.html](http://www.ubuntugeek.com/ubuntu-9-10-karmic-rc-released.html)

---

### Post by ranch hand on 2009-10-22
More to the point;
[https://lists.ubuntu.com/archives/ubuntu-announce/2009-October/000126.html](https://lists.ubuntu.com/archives/ubuntu-announce/2009-October/000126.html)
> 
Before installing or upgrading to Ubuntu 9.10 please review the instructions
and caveats in the release notes:

[http://www.ubuntu.com/getubuntu/releasenotes/910](http://www.ubuntu.com/getubuntu/releasenotes/910)

In addition, there are a small number of known bugs in the release candidate
that will be fixed before the Ubuntu 9.10 release, but warrant highlighting
for your attention:

[http://www.ubuntu.com/getubuntu/releasenotes/910overview#Known%20issues]("http://www.ubuntu.com/getubuntu/releasenotes/910overview#Known%20issues")

About The Release Candidate
---------------------------

The purpose of the Release Candidate is to solicit one last round of testing
before the final release. Here are ways that you can help:

 * Upgrade from Ubuntu 9.04 to the Release Candidate by following the 
   instructions in the release notes referenced above.

 * Participate in installation testing using the Release Candidate CD
   images, by following the testing and reporting instructions at
   [http://wiki.ubuntu.com/Testing/ISO](http://wiki.ubuntu.com/Testing/ISO)


---

