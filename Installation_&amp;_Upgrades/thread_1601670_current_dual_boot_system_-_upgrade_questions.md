---
title: "current dual boot system - upgrade questions"
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by kwildman on 2010-10-20
[LEFT]I am currently using Ubuntu 9.10 that is configured as a dual boot with Windows XP.   Unfortunately i need XP to provide IT Admin support on some of my systems.   

I would like to upgrade the Ubuntu to the newest version 10.10.   I know I have to upgrade to 10.04 first.    My question is if I do the upgrade through the System>Update manager will it keep my current dual boot configuration intact?  Both during the 9.1 > 10.04 and 10.04>10.10 upgrades?

I will clone the hard drive before doing anything but don't really have a lot of time to waste if it is likely to be an ugly ordeal.    Sorry if this has been asked previously - I did try searching but returned way too many hits with no relevance to my question.

Thanks in advance for any assistance.

kevin
[/LEFT]

---

### Post by oldfred on 2010-10-20
Anytime you upgrade/install systems you need good backups.

I used to upgrade in place (for about 3 years) and then did a clean install with Karmic. While I had to move /home to a separate partition and reinstall software, it housecleaned out years of cruft and worked so well that now I prefer clean installs.

Your upgrades should work and not change dual booting. Is your 9.10 a clean install with grub2? I prefer grub2 now that I have learned more about it, but it requires some effort to learn the new way. The biggest issue seems to be the new nouveau video that does not work for everyone without extra settings. I had to add nomodeset on the grub boot line before being able to boot & then installing the Nvidia driver. What video card do you have?

Some have not accepted the maintainers versions of config files and had huge issues as things do not work. If you have edited any config file in /etc make a backup so you can re-edit if necessary and always accept new versions of config files. Old setting may not even be required in some cases.

---

### Post by sikander3786 on 2010-10-20
If it is a critical type of system, I would recommend not to upgrade it. Or if you are prepared for all the troubles, you can try upgrading from 9.10 > 10.04 > 10.10 and if it breaks, do a clean install. Some members won't agree with me but, to be honest, upgrading has never worked for me. The more the number of packages installed, the lesser chances of a successful upgrade.

You can find many thread mentioning troubles upgrading from 10.04 > 10.10.

If the upgrade goes successfully, for sure you'll be left with a dual boot system.

The only thing I'll recommend is to save all you data and do a clean install with 10.10.

---

### Post by kwildman on 2010-10-20
Thanks.

I did install using a seperate home partition.  Is there a dummies guide to doing a fresh install that would leave my windows partition alone.   Do I just tell it to install to the existing partions and if I specify /home will it leave that intact?   

Sorry for all the questions but I am still a bit of a noob w/ linux.   

Best regards,

Kevin

---

### Post by oldfred on 2010-10-20
Yes. You need to use manual install and just choose the current linux partition to install / (root) to and what format. You also choose which partition is /home but DO NOT format it. Just be sure to choose the correct partitions. I have many and have installed to the wrong one.

If you have installed lots of apps you can make a list and use it to reinstall all the apps.

 dpkg --get-selections > ubuntu-files
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, the tip will only reinstall Ubuntu files,


All your user settings will be in /home but system settings are in config files in /etc.  If you have customized anything system wide you may want to back that file (or all of /etc) up also.

[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

---

### Post by kwildman on 2010-10-21
Thanks - that is what i thought but wanted to make sure.   I will be doing a clean install on my netbook first because the upgrade crapped.

I appreciate all the help.    You guys :guitar:

---

