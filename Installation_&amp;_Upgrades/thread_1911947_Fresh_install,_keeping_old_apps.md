---
title: "Fresh install, keeping old apps"
date: 2012-01-19
forum: Installation &amp; Upgrades
---

### Post by Nico-dk on 2012-01-19
I'm getting a new laptop within a week and will (of course) do a fresh install of Ubuntu, but I'd like to keep most apps and settings (like windows style, repos etc.) from my current 10.10 install.

How do I go about doing that?


I've searched for a solution, but pretty much every post on the subject of backing up boils down to: backup your home dir.
I was hoping to find something like apt-get backup, that would create a reference-file of sorts, which could be called on a fresh install perhaps using apt-get update/install from file.

Is this even possible?

---

### Post by Buntumatic on 2012-01-19
As any UNIX out there Ubuntu is multi-user system, even if there is only one user. Apt-get is a system tool, it will not dive into user level. All your customization is stored in your home directory, that's the only directory an user can write. Reusing it effectively will restore all your user settings. However, if there has been a major upgrade then your old conf may not be compatible any more, in that case you just need to start from scratch and do your customization.

---

### Post by ratcheer on 2012-01-19
You can keep most of your settings, but you will have to reinstall your apps. It is not too bad of a process.

1) If your /home is on your / (root) partition, you need to create a new partition and migrate /home to it.

2) Do an almost fresh install. When the partitioner runs, instruct it NOT to format the partition you put /home on.

3) Reinstall your apps. Your settings and most data (any data stored under /home) will still be intact.

Tim

---

### Post by oldfred on 2012-01-19
Your /home has all your user settings and program settings. Unless you specify otherwise it usually has all your data also.

But programs are not included. You can easily make a list and use that list to reinstall to a new release of Ubuntu. It will install the newer version of each app that is the supported version for that release.  Only if the app is obsolete will it not be installed. But you may want to edit list (it is just a text file) and remove some apps. I found I was still installing python2.5. They now have LibreOffice not OpenOffice and you probably do not want both.

My backup procedure is to do a clean install.
[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

 The part that exports a list of installed apps is the dpkg get selections and save to a file:
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

---

### Post by Nico-dk on 2012-01-20
Sorry, should've specified in the forst post;
I'm the only user, and I always keep my /home on a seperate partition (ext3).


> **oldfred said:**
> You can easily make a list and use that list to reinstall to a new release of Ubuntu.
Exactly what I was looking for, thanks.

---

