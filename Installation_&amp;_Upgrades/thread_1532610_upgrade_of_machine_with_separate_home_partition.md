---
title: "upgrade of machine with separate home partition"
date: 2010-07-16
forum: Installation &amp; Upgrades
---

### Post by candtalan on 2010-07-16
I will be helping a friend upgrade from 9.04 through to 10.04 LTS, and I am aware that the machine was installed with a separate home partition. I know a clean install is an option however I am tempted by online version upgrades with the thought that any apps they are using will be carried over. Is this a realistic hope? I know that medibuntu for example does not survive a version upgrade.

Comments appreciated

---

### Post by mörgæs on 2010-07-17
Since you have a separate /home, the clean install would be even easier to do. 

Especially when many apps are installed I would go for a clean install. The more complicated system, the riskier is upgrading.

---

### Post by bobpress on 2010-07-17
I have done upgrades and new installs in such a situation.  With a separate home partition, so long as you install the same user, do a custom format for partitions, and don't format the /home partition all data will be saved.  All your applications/programs will not, but the data and customizations will.

Here is the process that I have done.

Before doing an install backup a package list.  Make sure you have dpkg installed (can be done through Synaptic).   Then run this command (I call it packagelist.txt, but you can name it anything):

> dpkg --get-selections > packagelist.txtThis will put the entire list in packagelist.txt.  Save this file and make a backup copy on a USB drive.  After installation, again make sure dpkg is installed in the new installation.  You may need to edit the package list with gedit and remove some lines if there are some older kernels or other packages that you don't want installed in the new installation.  

You might also want to set in Synaptic Package Manager or Update Manager the repositories to include all of the ones downloadable from the internet since some of the programs they have installed could be proprietary or in the multiverse.  Then run this command in the directory where programlist.txt is located:

> dpkg --set-selections < packagelist.txtThis will set the list of install packages to the ones in the old installation.   To actually install the selections, use:

> apt-get -u dselect-upgrade

---

### Post by candtalan on 2010-07-17
Thank you each for your responses and information, much appreciated.

I have also, for testing, taken a spare machine and installed ubuntu 9.04 arranged with a separate /Home partition, I added a single jpeg picture and also installed digikam. 

I then did all updates, then accepted the online version upgrade to 9.10 (obviously as existing user).

After completion  at 9.10, the /Home was still in place, th ejpeg picture still in place, and digikam ran ok although complained about incomplete language support an dI accepted its offer of 'fix it now'

The experiment suggests that from 9.04 to 9.10, a simple installation is probably ok. I will aim to continue to do online version upgrade to 10.04 soon.

---

### Post by mörgæs on 2010-07-17
When the project is finished, you have probably used longer time testing and upgrading than it would have taken to install 10.04 and applications from scratch :-)

---

### Post by bobpress on 2010-07-17
> **candtalan said:**
> Thank you each for your responses and information, much appreciated.

I have also, for testing, taken a spare machine and installed ubuntu 9.04 arranged with a separate /Home partition, I added a single jpeg picture and also installed digikam. 

I then did all updates, then accepted the online version upgrade to 9.10 (obviously as existing user).

After completion  at 9.10, the /Home was still in place, th ejpeg picture still in place, and digikam ran ok although complained about incomplete language support an dI accepted its offer of 'fix it now'

The experiment suggests that from 9.04 to 9.10, a simple installation is probably ok. I will aim to continue to do online version upgrade to 10.04 soon.

If you check the upgrade pages for supported upgrades it's OK from 9.04 to 9.10 and from one LTS to the next LTS version, but upgrade from 9.04 to 10.04 LTS is not. [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) You could step upgrade 9.04 to 9.10 and then 9.10 to 10.04.  Of course, that would probably take longer than a new install and adding any programs back that aren't in Main and Universe repositories.

---

### Post by candtalan on 2010-07-18
> **candtalan said:**
>  The experiment suggests that from 9.04 to 9.10, a simple installation is probably ok. I will aim to continue to do online version upgrade to 10.04 soon.

latest test: the online version upgrade from the 9.10 to 10.04 went ok. The user file was retained, the directory structure was unchanged, and although when digikam was first run it did not complete starting, it did start normally on the next boot up.

Incidentally I have found an occasion when a direct install of 10.04 gave problems (gnome panels) whereas an upgrade from 9.10 did not. The target machine for my exercise here is not mine and I do not know how it will react for 10.04.

If an online version upgrade fails for whatever reason, I can fall back to a clean install.

My experience with 10.04 gnome panels is #18
[http://ubuntuforums.org/showthread.php?t=1471349&page=2](http://ubuntuforums.org/showthread.php?t=1471349&page=2)

---

