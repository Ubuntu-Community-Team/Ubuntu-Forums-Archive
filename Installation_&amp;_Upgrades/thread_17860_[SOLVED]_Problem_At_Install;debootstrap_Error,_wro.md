---
title: "[SOLVED] Problem At Install;debootstrap Error, wrongly burned ISO CD"
date: 2005-03-03
forum: Installation &amp; Upgrades
---

### Post by wojtalik on 2005-03-03
Hello!

Here is the way to overcome an installation problem which was mentioned by several people here. This message consists of description of the installation problem, the solution and a call for disucssion.

**Problem description:**

During the installation of base system the following error message appears:

"Problem At Install;debootstrap Error
[We're starting the install then getting this message:]
Installs the base system
Debootstrap Error
Couldn't retrieve gettext-base.This may be due to a network problem or a bad cd, depending on your installation method If you are installing from cd-r or cd-rw , burning the cd at a lower speed may help"

*(In place of "gettext-base" there may be any other application. I my case it was "Postfix").*

The problem was described in several messages in this forum, including:
[http://ubuntuforums.org/showthread.php?t=10423](http://ubuntuforums.org/showthread.php?t=10423)
[http://ubuntuforums.org/showthread.php?p=46207](http://ubuntuforums.org/showthread.php?p=46207)
[http://ubuntuforums.org/showthread.php?t=11785](http://ubuntuforums.org/showthread.php?t=11785)
[http://ubuntuforums.org/showthread.php?t=15011](http://ubuntuforums.org/showthread.php?t=15011)

**Solution:**

It does not help if you burn ISO CD with a smaller spead. It doesn't work if your CD was aready OK. To solve the problem you should format your partitions at the earlier stage of installation process.

As it was already mentioned in [this post](http://ubuntuforums.org/showpost.php?p=70084&postcount=18):

*"When selecting the partition(s) to use in the partition table, make sure that 'Usage method' is set to 'format the partition'. Mine was already formatted, but it seems Ubuntu installer wants to format it for itself. "*

**Call for disucussion:**

I think there are two things to be done in regard to this installation problem.

1. I am affraid that the error message is missleading. It encourages people to burn another ISO CD while the CD is not a problem at all! I propose that the error message should be changed in order to inform user that the problem may appear also because of problems with partitioning and disc formatting.

2. This error should not happen at all! If it is required by Ubuntu that the partitions are formatted, the user should be informed about it during partitioning part of the instalation. User should be warned that partitions will be formatted or there should be a message like: "partitions have to be formatted. Installation cannot be continued without formatting".

Do you think that this problem should be put into the [bugzilla](https://bugzilla.ubuntu.com/)  as a bug in Ubuntu?

Greetings, Marcin

---

