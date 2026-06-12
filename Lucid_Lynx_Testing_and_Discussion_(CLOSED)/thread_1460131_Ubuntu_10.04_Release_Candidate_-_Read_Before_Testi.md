---
title: "Ubuntu 10.04 Release Candidate - Read Before Testing!"
date: 2010-04-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by 23meg on 2010-04-22
Ubuntu 10.04 Release Candidate, which is the final milestone release leading to Ubuntu 10.04, has been released. Refer to the links below for more information:

[list] [*] [Release announcement]("https://lists.ubuntu.com/archives/ubuntu-announce/2010-April/000132.html") on the [ubuntu-announce mailing list]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-announce")
[*] [Technical Overview]("http://www.ubuntu.com/getubuntu/releasenotes/1004overview")[/list]

If you're new to testing Ubuntu, and are running Lucid for the first time with the RC, the tips below will be especially useful for you. Please take time to read them.

[list]

[*] If you're having a problem with the RC, or are curious about a certain feature, change or malfunction, you're most likely not alone. Please do a forum search before starting new threads. This is very simple with the "Search this Forum" function on the upper right side of the forum index.


[IMG]http://img718.imageshack.us/img718/2897/screenshotxs.png[/IMG]

Click it, type some keywords related to what you're looking for, and if you see relevant threads come up, please post to those threads instead of starting a new thread. Remember that the best way to provide feedback and help improve Ubuntu is to **file bug reports on the issues you're experiencing**, and improve existing reports if they've been filed. 

**Please don't post your feedback on the RC straight to this forum**. Forums are not a good way to keep track of issues, and your post will not be read by the relevant people who can fix your problems. Instead, do a search to find if there's a thread related to your issue(s), and if not, start a new thread, check if others are experiencing the same issue(s), and make sure a bug report is filed (doing a forum search, and/or [a search on the bug tracker]("https://bugs.launchpad.net/ubuntu/") is a good idea). If not, and you need help with [filing a bug report]("https://help.ubuntu.com/community/ReportingBugs"), don't hesitate to ask for help!


[*] **If you install the RC, you can later upgrade to the final release without having to do a fresh install**. But there may be some drawbacks in certain scenarios; refer to [the sticky thread on common problems and frequently asked questions]("http://ubuntuforums.org/showthread.php?t=1343449") for details.


[*] The milestone releases (alphas, the beta and the RC) are snapshots of the package archive at their pre-decided release dates. **If you have the latest updates installed on your testing installation, you don't have to remove your current testing installation and install the RC**, unless you want to test installation-specific components (the installer, bootloader etc.), or your installation is affected by potential corner cases that may arise during the development cycle that require a reinstall to fix. Refer to [the sticky thread on common problems and frequently asked questions]("http://ubuntuforums.org/showthread.php?t=1343449") for further details.


[*] If you're just starting to test Lucid, please read the [technical overview]("http://www.ubuntu.com/getubuntu/releasenotes/1004overview") and see if you're affected by any of the known bugs, take a look at [this wiki page]("https://wiki.ubuntu.com/UbuntuDevelopment/UsingDevelopmentReleases"), and [the sticky thread on common problems and frequently asked questions]("http://ubuntuforums.org/showthread.php?t=1343449") for information on various testing methods and good practices. 


[*] Once you've started testing, **exercise caution when upgrading packages** - in special, avoid partial upgrades offered by Update Manager unless you know precisely why it's offering a partial upgrade. Regardless of which tool (APT, Update Manager, Synaptic, Aptitude) you're using to upgrade your packages, **always check the list of packages to be removed, upgraded and installed before each upgrade**. If in doubt, check the changelogs ("Package > Download Changelog" in Synaptic, or "aptitude changelog package_name", or at [packages.ubuntu.com]("http://packages.ubuntu.com")) to see why a package may be being removed. If packages are held back, wait until they're installable again. Refer to [the sticky thread on partial upgrades]("http://ubuntuforums.org/showthread.php?t=1343434") for further information.
[/list]


**Downloads**

(Please prefer torrents, and [using rsync / zsync]("https://help.ubuntu.com/community/RsyncCdImage")).

To upgrade to Ubuntu 10.04 LTS RC from Ubuntu 9.10 or Ubuntu 8.04 LTS, follow [these instructions]("https://help.ubuntu.com/community/LucidUpgrades"). Or, download Ubuntu 10.04 RC here (choose the mirror closest to you):

  Africa:

    * [http://bw.releases.ubuntu.com/10.04](http://bw.releases.ubuntu.com/10.04) (Botswana)
    * [http://ls.releases.ubuntu.com/10.04](http://ls.releases.ubuntu.com/10.04) (Lesotho)
    * [http://mz.releases.ubuntu.com/10.04](http://mz.releases.ubuntu.com/10.04) (Mozambique)
    * [http://na.releases.ubuntu.com/10.04](http://na.releases.ubuntu.com/10.04) (Namibia)
    * [http://ubuntu.mirror.ac.za/ubuntu-release/10.04](http://ubuntu.mirror.ac.za/ubuntu-release/10.04) (South Africa)

  Asia:

    * [http://ubunturelease.hnsdc.com/10.04](http://ubunturelease.hnsdc.com/10.04) (India)
    * [http://ubuntutym2.u-toyama.ac.jp/ubuntu/10.04](http://ubuntutym2.u-toyama.ac.jp/ubuntu/10.04) (Japan)
    * [http://ubuntu.qualitynet.net/releases/10.04](http://ubuntu.qualitynet.net/releases/10.04) (Kuwait)
    * [http://ftp.mtu.ru/pub/ubuntu/releases/10.04](http://ftp.mtu.ru/pub/ubuntu/releases/10.04) (Russian Federation)
    * [http://mirror.yandex.ru/ubuntu-releases/10.04](http://mirror.yandex.ru/ubuntu-releases/10.04) (Russian Federation)
    * [http://ubuntu.mirrors.isu.net.sa/releases/10.04](http://ubuntu.mirrors.isu.net.sa/releases/10.04) (Saudi Arabia)
    * [http://ftp.linux.org.tr/ubuntu-releases/10.04](http://ftp.linux.org.tr/ubuntu-releases/10.04) (Turkey)

  Europe:

    * [http://ubuntu.ipacct.com/releases/10.04](http://ubuntu.ipacct.com/releases/10.04) (Bulgaria)
    * [http://hr.releases.ubuntu.com/10.04](http://hr.releases.ubuntu.com/10.04) (Croatia)
    * [http://mirrors.dotsrc.org/ubuntu-cd/10.04](http://mirrors.dotsrc.org/ubuntu-cd/10.04) (Denmark)
    * [http://ftp.estpak.ee/pub/ubuntu-releases/10.04](http://ftp.estpak.ee/pub/ubuntu-releases/10.04) (Estonia)
    * [http://www.nic.funet.fi/pub/mirrors/releases.ubuntu.com/10.04](http://www.nic.funet.fi/pub/mirrors/releases.ubuntu.com/10.04) (Finland)
    * [http://ftp.oleane.net/ubuntu-cd/10.04](http://ftp.oleane.net/ubuntu-cd/10.04) (France)
    * [http://ubuntu.mirror.tudos.de/ubuntu-releases/10.04](http://ubuntu.mirror.tudos.de/ubuntu-releases/10.04) (Germany)
    * [http://ftp.uni-kl.de/pub/linux/ubuntu.iso/10.04](http://ftp.uni-kl.de/pub/linux/ubuntu.iso/10.04) (Germany)
    * [http://speglar.simnet.is/ubuntu-releases/10.04](http://speglar.simnet.is/ubuntu-releases/10.04) (Iceland)
    * [http://ftp.heanet.ie/pub/ubuntu-releases/10.04](http://ftp.heanet.ie/pub/ubuntu-releases/10.04) (Ireland)
    * [http://releases.ubuntu.fastbull.org/ubuntu-releases/10.04](http://releases.ubuntu.fastbull.org/ubuntu-releases/10.04) (Italy)
    * [http://nl.releases.ubuntu.com/releases/10.04](http://nl.releases.ubuntu.com/releases/10.04) (Netherlands)
    * [http://no.releases.ubuntu.com/10.04](http://no.releases.ubuntu.com/10.04) (Norway)
    * [http://ftp.vectranet.pl/ubuntu-releases/10.04](http://ftp.vectranet.pl/ubuntu-releases/10.04) (Poland)
    * [http://mirrors.fe.up.pt/pub/ubuntu-releases/10.04](http://mirrors.fe.up.pt/pub/ubuntu-releases/10.04) (Portugal)
    * [http://mirrors.xservers.ro/ubuntu/releases/10.04](http://mirrors.xservers.ro/ubuntu/releases/10.04) (Romania)
    * [http://ftp.antik.sk/ubuntu-releases/10.04](http://ftp.antik.sk/ubuntu-releases/10.04) (Slovakia)
    * [http://ubuntu.cica.es/releases/10.04](http://ubuntu.cica.es/releases/10.04) (Spain)
    * [http://se.releases.ubuntu.com/10.04](http://se.releases.ubuntu.com/10.04) (Sweden)
    * [http://mirror.switch.ch/ftp/mirror/ubuntu-cdimage/10.04](http://mirror.switch.ch/ftp/mirror/ubuntu-cdimage/10.04) (Switzerland)

  North America:

    * [http://archaea.its.sfu.ca/mirror/ubuntu-releases/10.04](http://archaea.its.sfu.ca/mirror/ubuntu-releases/10.04) (Canada)
    * [http://mirror.csclub.uwaterloo.ca/ubuntu-releases/10.04](http://mirror.csclub.uwaterloo.ca/ubuntu-releases/10.04) (Canada)
    * [http://mirror.anl.gov/pub/ubuntu-iso/CDs/10.04](http://mirror.anl.gov/pub/ubuntu-iso/CDs/10.04) (United States)
    * [http://ubuntu.cs.utah.edu/releases/10.04](http://ubuntu.cs.utah.edu/releases/10.04) (United States)
    * [http://ubuntu-releases.cs.umn.edu/10.04](http://ubuntu-releases.cs.umn.edu/10.04) (United States)
    * [http://www.gtlib.gatech.edu/pub/ubuntu-releases/10.04](http://www.gtlib.gatech.edu/pub/ubuntu-releases/10.04) (United States)

  Oceania/Australia:

    * [http://ubuntu-releases.optus.net/10.04](http://ubuntu-releases.optus.net/10.04) (Australia)
    * [http://ftp.citylink.co.nz/ubuntu-releases/10.04](http://ftp.citylink.co.nz/ubuntu-releases/10.04) (New Zealand)
    * [http://mirror.ihug.co.nz/ubuntu-releases/10.04](http://mirror.ihug.co.nz/ubuntu-releases/10.04) (New Zealand)

  South America:

    * [http://ubuntu.c3sl.ufpr.br/releases/10.04](http://ubuntu.c3sl.ufpr.br/releases/10.04) (Brazil)
    * [http://espelhos.edugraf.ufsc.br/ubuntu-releases/10.04](http://espelhos.edugraf.ufsc.br/ubuntu-releases/10.04) (Brazil)
    * [http://www.las.ic.unicamp.br/pub/ubuntu-releases/10.04](http://www.las.ic.unicamp.br/pub/ubuntu-releases/10.04) (Brazil)

  Rest of the world:

    [http://releases.ubuntu.com/10.04](http://releases.ubuntu.com/10.04) (Great Britain)

---

### Post by filip007 on 2010-04-22
I'm having notification area problem....

After i did input location and weather and restart because nothing happened and get error.

[[IMG]http://img215.imageshack.us/img215/2028/screenshotrt.th.jpg[/IMG]](http://img215.imageshack.us/i/screenshotrt.jpg/)

After another reset no problem any more...

---

### Post by eyelessfade on 2010-04-22
In the Known Issues:
> LVM, RAID, or encrypted block devices are incorrectly limited to 2TiB. This issue will be resolved for the 10.04 LTS release. [(543838)]("https://bugs.launchpad.net/ubuntu/+source/parted/+bug/543838"))

Is this problem only effecting creations of new volumes or may it be a problem to upgrade from karmic to lucid with a raid volume grater then 2TiB?

Usually I upgrade my main computer with alpha, but with a software raid I have been reluctant to do so...

---

### Post by djchandler on 2010-04-23
> **eyelessfade said:**
> In the Known Issues:

Is this problem only effecting creations of new volumes or may it be a problem to upgrade from karmic to lucid with a raid volume grater then 2TiB?

Usually I upgrade my main computer with alpha, but with a software raid I have been reluctant to do so...

I gather it affects both pre-existing volumes as well as creating new volumes. That may not be entirely so if you upgrade your installation in place rather than create a new installation and then try to have the new installation mount your pre-existing volumes. I did not see where anyone posted that they upgraded from Karmic or Hardy. The feedback posted in the Launchpad thread was gathered from apparently fresh installs. Take what I wrote about upgrading in place with a grain of salt. I could be wrong.

The fix was submitted 2 days after the RC ISO images available now were created. The fix will be available on the Final Release ISO. Considering the amount of work that seems to be necessary to work around this and the amount of data at stake, perhaps you will want to wait to install Lucid when the Final Release becomes available next week.

---

### Post by eyelessfade on 2010-04-23
> **djchandler said:**
> Considering the amount of work that seems to be necessary to work around this and the amount of data at stake, perhaps you will want to wait to install Lucid when the Final Release becomes available next week.
Indeed, I'll just have to use my other systems to be beta/rc tester :)

---

### Post by schmolch on 2010-04-24
How do i file a bug if Lucid does not even boot?

---

### Post by WitchCraft on 2010-04-24
> **schmolch said:**
> How do i file a bug if Lucid does not even boot?

Simple, format windows, then the Lucid bugs are gone.

Windows writes hibernate info into the Linux boot sector...

But you'll have to reinstall.

---

### Post by schmolch on 2010-04-24
> **WitchCraft said:**
> Simple, format windows, then the Lucid bugs are gone.

Windows writes hibernate info into the Linux boot sector...

But you'll have to reinstall.

Go to a rehab-center asap.

---

### Post by WitchCraft on 2010-04-26
> **schmolch said:**
> Go to a rehab-center asap.

:lolflag:

Does it not boot into X or not boot at all ?

---

### Post by schmolch on 2010-04-26
> **WitchCraft said:**
> :lolflag:

Does it not boot into X or not boot at all ?

It is booting now.
My Usb-Hub caused i/o errors and my bios boots from usb only if the planets are alligned.

---

### Post by Nelsinius on 2010-04-27
I recently downloaded and installed the 10.04 Release Candidate. In 2 occasions in 2 different computers I encountered a problem after using the "Log Out" button. Both computers went dark and stopped responding, which required a forced re-start (I might be using the wrong nomenclature). I wonder if anyone else has also experienced this event.

---

### Post by andrewabc on 2010-04-27
I was running liveusb of RC.

It's now normal/default for ubuntu to have 4 virtual desktops? It always had two. Not complaining, just something I only noticed now.

---

### Post by israelrt on 2010-04-27
> **andrewabc said:**
> I was running liveusb of RC.

It's now normal/default for ubuntu to have 4 virtual desktops? It always had two. Not complaining, just something I only noticed now.

It Linux, it is configurable.
For amusement, I just set it to 100 virtual desktops.

---

### Post by eltonw on 2010-04-28
I have downloaded the RC iso and burnt it to DVD. Loading it as a *[COLOR="DarkRed"]**live CD**[/COLOR]* on my Asus EEE 1000 PC, **[COLOR="DarkGreen"]it still fails to connect[/COLOR]**:(, as previously reported WRT Beta 1 and Beta 2.
SEE:[http://ubuntuforums.org/showthread.php?t=1438175]("http://ubuntuforums.org/showthread.php?t=1438175")

... related thread HERE:[http://ubuntuforums.org/showthread.php?p=9120466#post9120466]("http://ubuntuforums.org/showthread.php?p=9120466#post9120466")

---

