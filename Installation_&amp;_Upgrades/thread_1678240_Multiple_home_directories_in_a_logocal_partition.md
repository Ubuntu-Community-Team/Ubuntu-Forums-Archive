---
title: "Multiple home directories in a logocal partition?"
date: 2011-01-30
forum: Installation &amp; Upgrades
---

### Post by daksai3 on 2011-01-30
Urgent-ish

Ok i want to install multiple Linux distributions (about 7 lol). At first I was thinking of using one /home in a partition for all of them but after some investigating I found out that it does not work. Now I'm wondering whether or not it is possible to create multiple home directories in a logical partition. I basically want to create folders or directories within a partition and then mount them as the /home for each of the different distributions. Is this possible? 

What format should it be? I keep hearing ext3 as being better than ext4, is that true?

---

### Post by oldfred on 2011-01-30
You can install multiple /home but I would just keep /home inside each root install and create one common /data partition. Then you can share the data with each install. The only issue with a common /data can be different distributions may have different user numbers. If all Debian based it is not an issue. If data is to be shared with windows then NTFS is better and it does not have any Linux ownership or permissions - both good & bad. Not really recomended unless you are using windows so when you have issues you can run chkdsk as Linux does not have a way to run chkdsk.

Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition")

kansasnoob's sharing and Morbius1 use of bindfs
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)
HowTo: Create shared directory for local users (with bindfs).
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)
Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments - now mounting as /mnt/data as better location.
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

More info on gid & uid
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

---

### Post by srs5694 on 2011-01-30
> **daksai3 said:**
> Ok i want to install multiple Linux distributions (about 7 lol). At first I was thinking of using one /home in a partition for all of them but after some investigating I found out that it does not work.

It does work. It works best if you create separate home directories for each distribution and user. For instance, if you're the only user, you might use /home/daksai_ubuntu for Ubuntu, /home/daksai_fedora for Fedora, and so on. This keeps your configuration files (for GNOME, Firefox, and so on) for each distribution from tromping on each other, which is the biggest potential pitfall with a single /home partition.

The easiest way to achieve this goal is to use different usernames for each installation; however, it's possible to set up a username to use a home directory that's not named after the user. Thus, you could use daksai as your username in all distributions, but with a different home directory for each. Precisely how you set this up at installation varies from one distribution to another (I don't think Ubuntu's got an option to do this). It may be simpler to just create different usernames at installation and then rename the user (with the "usermod" command or GUI equivalents) after installation.

You can use one distribution's home directory as the "master" and create symbolic links to it in the others for easier file management. (This will require coordinating UID values across installations, though.)

Oldfred's suggestion will also work; however, IMO it offers no advantages over using a single /home partition with separate subdirectories for each installation, and doing it as I suggest is a more traditional Unix/Linux solution that's slightly more elegant. A separate /data partition is "the Windows way," whereas a single /home partition is "the Linux way." The reason your research suggested that it wasn't possible was that too many people whose posts, blogs, or whatever you read came too recently from the Windows world, and so still think in "the Windows way."

---

