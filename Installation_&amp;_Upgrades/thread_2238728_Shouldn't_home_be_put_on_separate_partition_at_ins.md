---
title: "Shouldn't /home be put on separate partition at install?"
date: 2014-08-09
forum: Installation &amp; Upgrades
---

### Post by bruce-euphon on 2014-08-09
I am in a Catch-22 with upgrading from 12.04 to something newer. I have untrusted packages that cause Software Centre to fail and I have a package which Software Updater and Synanapric Package Manager refuse to remove. I probably need to reinstall Ubuntu.

Now, I know that Software Updater has an update option. It says that I can update my system to 12.10, not the LTS path of 12.04-05, I think it is called. My understanding was that I had three years of support when I installed 12.04, but it effectively is seeming like 18 months, or less, and 12.10 is not LTS.

So, since it seems that Ubuntu wants you to reinstall frequently, and upgrade becomes problematic because of packages dropped from repositories, it makes sense to me that the install should give you the option to slice up the free space on your disk so that /home is a separate partition, so that when you are forced to reinstall you don't run the risk of clobbering your homw dir between installs. I know that I can do this by hand and use gparted or something similar to carve out some free space, and I know that I have to make sure that the entry is /etc/fstab is there to mount the partition at boot time, but I think that given the frequency at which Ubuntu wants to be reinstalled that these tasks should be handled at install time. An option should be shown that says in the free space found on the disk, or from the whole disk, that an effort will be made to create THREE partitions, one for /, one for /home, and one for a swap partition. Futhermore if the task is reinstall that the installer will at least recommend that /home be put into a separate partition and make an educated guess about how big it should be, It should allow the user to say that he wants to use the space available or any unused partitons for creating a separate /home and then proceed to do a fresh install on what is mounted at /.

I think that thrusting Ubuntu users into what is system administration territory because of gaps in the package management is a real gotcha and as compared to the competition, notablly OS X, is a vulnerability to Linux. At least a little effort at install or re-install could help users who do not use low-level commands and all their underlying complexity; and especially when the package management system causes failures due to decisions about packages that are dropped with no warning for the user.

---

### Post by em3raldxiii on 2014-08-09
Actually, the installer does give you the option to carve up your drive into different partitions, it's essentially the same as using gParted, just during the install instead of its own process in and of itself.  It's been there since ... well, as long as I can remember, and I started with 5.10.

But there are a couple of problems with doing it that way, so you have to be smart.  One such problem is that if you use the same username with your new install, then it will pick up the old ~/ directory, including all of the hidden config files.  This sounds like a good thing, except that any problems that originated there will then affect your new install.  So what I have done in the past is used a slightly different username (Mike versus Michael, for example), and then just manually hunted down the important files on the ~/ partition.  Doing it the way Ubuntu currently does with its automagic installer avoids these types of problems.  Besides, if the partition is on the same physical disk as the / partition, and you are making any changes to the / partition, it's still recommended that you back up all of your files, so if you're going to do that anyway ...

Finally, you probably don't have to reinstall -- in fact, I strongly discourage it, even though I have done it that way in the past.  If you have broken packages, you can sometimes fix them with a **sudo apt-get install -f **which "fixes" broken packages.  Of course, you certainly can reinstall, and sometimes it's nice to start fresh.  I usually kick myself, though, because I discover just how much I had my system tweaked to my own preferences only after it's too late.

---

### Post by kansasnoob on 2014-08-09
First things first; do NOT upgrade to 12.10 because it's already EOL:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Open Update Manager, click on Settings, and under the Updates tab at the bottom of the page toggle *Notify me of a new version* to "For long term support versions". For some reason (probably more than one reason) upgrade notifications were delayed/disabled:

[https://bugs.launchpad.net/ubuntu-release-notes/+bug/1351826](https://bugs.launchpad.net/ubuntu-release-notes/+bug/1351826)

[https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/1344762](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/1344762)

According to the latter:

> The meta-release file will be updated on Monday, August 11th.

Second it would be worth investigating what's wrong with your current installation. Maybe you got caught in HWE EOL hell:

[https://wiki.ubuntu.com/1204_HWE_EOL](https://wiki.ubuntu.com/1204_HWE_EOL)

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

LTS users do need to be aware to avoid that in the future by avoiding point releases beyond the first one:

[http://ubuntuforums.org/showthread.php?t=2236096&page=2&p=13082770#post13082770](http://ubuntuforums.org/showthread.php?t=2236096&page=2&p=13082770#post13082770)

So let us have a look at what errors you're encountering and maybe we can just fix things ;)

---

### Post by grahammechanical on 2014-08-09
> [COLOR=#000000]given the frequency at which Ubuntu wants to be reinstalled[/COLOR]

In truth we have the choice of installing an LTS version and get options to upgrade at 2 years and then 4 years when the latest LTS is released or wait until the LTS is near end of life and upgrade to the latest released LTS.

People should not install the in-between releases unless they are prepared to upgrade every 6 or 7 months because the in-between releases only have 9 months support. That reduced level of support was a compromise due the Owner of Canonical wanting to drop in-between releases altogether.

The need to re-install often comes about because users like to mess around with the OS. And that can and often does mess things up.

Keep in mind that people buy computers with an OS pre-installed. And installing Linux is problematic anyway because manufacturers are not interested in making it easy to install another OS on the machines they sell.

Add in the fact that millions of computer buyers would not know how to install an OS even on a machine without an OS pre-installed and we are in a situation where the install process has to be simple and require only the limited amount of user input necessary. It would be off putting otherwise.

The developers are making the best of a bad job.

> [COLOR=#000000]An option should be shown that says in the free space found on the disk[/COLOR]

There would not be any free space. The pre-installed OS would be using all of it.  So, we are already at the point where the potential new user has to know how the resize the existing partitions.

Regards.

---

### Post by ian-weisser on 2014-08-10
> **bruce-euphon said:**
> upgrade becomes problematic because of packages dropped from repositories

Packages are dropped *only* when they are orphaned and unmaintained. Not Ubuntu's fault.
Your problem with 'untrusted' packages sounds like a PPA or other non-Ubuntu software problem. Also, by definition, not Ubuntu's fault.

You can make your upgrade process much safer and error-free by:

1) Back up your data. Back up your entire /home if you wish. How much do you value your data? The package manager won't remove anything from /home, and the installer, if it detects a /home directory, will preserve it...but what if (for whatever reason) the installer cannot detect it? How much is your data worth to you?

2) Uninstall non-Ubuntu software (including PPAs) before the upgrade. Reinstall afterward, if you still need it. It's *not Ubuntu software*. It's not supported, and the package manager is not psychic.

3) Restore any meta-packages (like ubuntu-desktop) that you may have removed elements of. Major desktop upgrades and applications changes need that metapackage to know that's the migration path you want. Without the meta-package, the package manager will properly assume you don't want those big changes.

Before you wash your car, close the windows.
Similar simple precautions apply here.

---

