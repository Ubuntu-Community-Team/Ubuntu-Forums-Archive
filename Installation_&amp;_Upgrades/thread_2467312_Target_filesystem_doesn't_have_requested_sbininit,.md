---
title: "Target filesystem doesn't have requested /sbin/init, /bin/sh:0:Can't open text"
date: 2021-09-23
forum: Installation &amp; Upgrades
---

### Post by sdancer75 on 2021-09-23
Hi, after updating 14.04 to 15 I can not boot any more even in recovery console. 

Target filesystem doesn't have requested /sbin/init
 /bin/sh:0:Can't open text
[ 3.536076] Kernel panic - not syncing : Attempted to kill ....

.............

[ 3.601600] ---- [ end kernel panic -- not syncing : ....]

Is there any way to fix it?

[IMG]https://i.ibb.co/vP66h5m/thumbnail.jpg[/IMG]

---

### Post by guiverc on 2021-09-23
Ubuntu 14.04 LTS reached the end of it's *standard support* some time ago - [https://fridge.ubuntu.com/2019/05/02/ubuntu-14-04-trusty-tahr-reached-end-of-life-on-april-25-2019-esm-available/](https://fridge.ubuntu.com/2019/05/02/ubuntu-14-04-trusty-tahr-reached-end-of-life-on-april-25-2019-esm-available/)

Ubuntu 15?   there is no Ubuntu 15, as the *year *format releases didn't start till 16 (or 2016), and that format is used for different products (eg. Ubuntu Core 16) as they are *snap* only, where as the *year.month* format products like 14.04 are *deb* package based. 

If you're talking about Ubuntu 15.04 - it reached EOL in 2016 - [https://fridge.ubuntu.com/2016/01/14/ubuntu-15-04-vivid-vervet-reaches-end-of-life-on-february-4-2016/](https://fridge.ubuntu.com/2016/01/14/ubuntu-15-04-vivid-vervet-reaches-end-of-life-on-february-4-2016/)

If you're talking about Ubuntu 15.10 - it too reached EOL in 2016 - [https://fridge.ubuntu.com/2016/07/28/ubuntu-15-10-wily-werewolf-end-of-life-reached-on-july-28-2016/](https://fridge.ubuntu.com/2016/07/28/ubuntu-15-10-wily-werewolf-end-of-life-reached-on-july-28-2016/)

Ubuntu *release-upgrade* tools won't upgrade you to an EOL release; so upgrading to either of those became impossible in mid-2016.

Ubuntu 16.04 LTS was a possible upgrade step too from 14.04; but it's *standard support* cycle has ended as well, with it supported only via ESM.  [https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/](https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/)

Ubuntu 15 though is not a *valid* release; there has been no path possible from 14.04 to either 15.04 or 15.10 since 2016, so I'd confirm what was actually done as what you describe implies it was forced, and how forced may provide clues..

I'd suggest booting *live* media & checking for issues there (`fsck` etc) and confirm what you did (looking in logs etc) as what you describe isn't possible using Ubuntu tools since mid-2016 using officially supported tools.   If the system was forced shutdown, the `fsck` will likely allow a normal boot to occur next time anyway (*assuming it finds issues & fixes them*)

---

### Post by sdancer75 on 2021-09-23
running (before the crash) the command **lsb_release -a **it reported 15.04 (vivid) version. Is that possible with Live CD to check the actual release version  ie [COLOR=#111111][FONT=Menlo]cat /etc/os-release[/FONT][/COLOR]? 

I have access to the boot disk thru this. I am not sure I think I run the command "[COLOR=#111111][FONT=monospace]do-release-upgrade"[/FONT][/COLOR]

---

### Post by ajgreeny on 2021-09-23
Trying to upgrade the distro version from either of the 15.# releases is pointless and probably doomed to failure! The do release upgrade path has closed for the 15.# versions so will simply fail.

As said above, both of those versions lost any support way back in 2016, five years ago, and 3v3n if you could sensibly upgrade from 15.10 to the following LTS version, 16.04, that has also lost support so the move will be of no real help.

Save yourself a lot of time, trouble and frustration by downloading the most recent LTS version, 20.04, in whichever DE version you prefer and install that.  It should take you no more than 15-20 minutes, give you a totally clean start and make life a lot simpler.

---

### Post by sdancer75 on 2021-09-23
> **ajgreeny said:**
> Trying to upgrade the distro version from either of the 15.# releases is pointless and probably doomed to failure! The do release upgrade path has closed for the 15.# versions so will simply fail.

As said above, both of those versions lost any support way back in 2016, five years ago, and 3v3n if you could sensibly upgrade from 15.10 to the following LTS version, 16.04, that has also lost support so the move will be of no real help.

Save yourself a lot of time, trouble and frustration by downloading the most recent LTS version, 20.04, in whichever DE version you prefer and install that.  It should take you no more than 15-20 minutes, give you a totally clean start and make life a lot simpler.

Can I upgrade to v20.04 at this point using an external usb/cd iso image? Does this will keep my old configurations, account etc?

Thanks

---

### Post by ActionParsnip on 2021-09-23
I'd suggest wiping the install off and doing a clean install of Focal (Ubuntu 20.04). You can restore your user data from your backups. You'll have a cleaner OS. If you upgrade you will need to upgrade through many different releases which will take a lot of time and a lot of data being pulled down from the web.

---

### Post by guiverc on 2021-09-23
You haven't said if this is a desktop or server install.

Ubuntu (& *flavor*) desktop installs have a feature that re-installs without touching configs.  This is usually done when there are package problems due to user errors, and you need to re-install the same release as its usually faster than fixing all the issues, but can also be used if you want to skip a release in upgrade (*like you*) and is actually far faster than a normal *release-upgrade*. use.

Boot the install media you want to install; start installer and use the *Manual Partitioning* option (or *Something else*). Assuming you're using a `ubiquity` or `calamares` installer ..

- select your existing partition(s) but **ensure you do not format** any  (*it's the no-format that triggers this upgrade via re-install*)
- the installer will note what package(s) you have installed
- erase system directories
- install new system (*from installation media*)
- attempt to add the additional packages you had added to your system (*noted earlier*) if they are available in Ubuntu repositories for your new release
- will **not **touch any user file/config (*unless in system directories; these got wiped - why it's not great with the server systems*); desktop apps store their data in $HOME which isn't touched ([I]unless you selected format)
[/I]- user is asked to reboot (*though warning is given if any package(s) weren't available in the new release; which I'd expect with a jump as large as what you're going to do*)

Issues can be the jump is so big, the programs may have had changes to how they stored data (eg. I used an application that did this; if you jumped 12.04->14.04->16.04->18.04->20.04 that would be handled in those steps; likewise if you'd gone through every release, but you've gone outside of that); so those apps may lose data because the *newer* version  cannot deal with the data you have (*given you skipped the release that handled the change*).  

To ensure this won't impact you involves a fair amount of homework (ie. *checking what apps matter to you, that they didn't require specific changes that meant you can't skip an upgrade - it' a lot of work*).  In these cases I'd just restore the data from your backups; but that may not help much either given it's the data itself that missed the upgrade done on a prior skipped release.  These issues though are **rare** (*I've only encountered issues once I that I remember; where the later release used a different database format & I'd skipped the database-conversion step*...) but are real if you rely on specific programs.  

If it really worries you, put a copy of your data on a VM & *testbox* and perform this type of install there to ensure issues won't impact you (this is faster than the homework required given it's not Ubuntu release notes that provide the specific warnings, but often the program release notes themselves that contain these warnings; *which is a lot of release notes between the version you were on and what you're jumping to.*..).

The system directory wipes create the complications for server programs/installations.  But this works really well with desktop systems  (I use it at least once per week though that's usually for QA or *Quality Assurance* purposes).  I mentioned `ubiquity` & `calamares` installers as that's where I QA test this; ie. I can't recall ever using it with *debian installer* and know I haven't with `subiquity` but they may also handle this too(*don't forget system directory issue*)

---

### Post by sdancer75 on 2021-09-24
> **guiverc said:**
> You haven't said if this is a desktop or server install.

Ubuntu (& *flavor*) desktop installs have a feature that re-installs without touching configs.  This is usually done when there are package problems due to user errors, and you need to re-install the same release as its usually faster than fixing all the issues, but can also be used if you want to skip a release in upgrade (*like you*) and is actually far faster than a normal *release-upgrade*. use.

Boot the install media you want to install; start installer and use the *Manual Partitioning* option (or *Something else*). Assuming you're using a `ubiquity` or `calamares` installer ..

- select your existing partition(s) but **ensure you do not format** any  (*it's the no-format that triggers this upgrade via re-install*)
- the installer will note what package(s) you have installed
- erase system directories
- install new system (*from installation media*)
- attempt to add the additional packages you had added to your system (*noted earlier*) if they are available in Ubuntu repositories for your new release
- will **not **touch any user file/config (*unless in system directories; these got wiped - why it's not great with the server systems*); desktop apps store their data in $HOME which isn't touched ([I]unless you selected format)
[/I]- user is asked to reboot (*though warning is given if any package(s) weren't available in the new release; which I'd expect with a jump as large as what you're going to do*)

Issues can be the jump is so big, the programs may have had changes to how they stored data (eg. I used an application that did this; if you jumped 12.04->14.04->16.04->18.04->20.04 that would be handled in those steps; likewise if you'd gone through every release, but you've gone outside of that); so those apps may lose data because the *newer* version  cannot deal with the data you have (*given you skipped the release that handled the change*).  

To ensure this won't impact you involves a fair amount of homework (ie. *checking what apps matter to you, that they didn't require specific changes that meant you can't skip an upgrade - it' a lot of work*).  In these cases I'd just restore the data from your backups; but that may not help much either given it's the data itself that missed the upgrade done on a prior skipped release.  These issues though are **rare** (*I've only encountered issues once I that I remember; where the later release used a different database format & I'd skipped the database-conversion step*...) but are real if you rely on specific programs.  

If it really worries you, put a copy of your data on a VM & *testbox* and perform this type of install there to ensure issues won't impact you (this is faster than the homework required given it's not Ubuntu release notes that provide the specific warnings, but often the program release notes themselves that contain these warnings; *which is a lot of release notes between the version you were on and what you're jumping to.*..).

The system directory wipes create the complications for server programs/installations.  But this works really well with desktop systems  (I use it at least once per week though that's usually for QA or *Quality Assurance* purposes).  I mentioned `ubiquity` & `calamares` installers as that's where I QA test this; ie. I can't recall ever using it with *debian installer* and know I haven't with `subiquity` but they may also handle this too(*don't forget system directory issue*)

Thank you for your reply. The version currently mounted to sda2 is show below. Does not say if its a server or desktop edition but I suppose since it had GUI is desktop

NAME="Ubuntu"
VERSION="15.04 (Vivid Vervet)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 15.04"
VERSION_ID="15.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"

---

