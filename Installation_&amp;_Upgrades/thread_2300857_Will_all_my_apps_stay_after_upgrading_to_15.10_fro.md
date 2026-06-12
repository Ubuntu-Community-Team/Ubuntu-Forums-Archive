---
title: "Will all my apps stay after upgrading to 15.10 from 15.04?"
date: 2015-10-28
forum: Installation &amp; Upgrades
---

### Post by javierdl on 2015-10-28
I am nervous about upgrading as I had spent quite some time transitioning to Ubuntu from Windows. Most things work, and I am very happy with what I've got now. So I definitely don't want to mess it up.

Thanks guys,

JDL

---

### Post by ubfan1 on 2015-10-28
The apps you got from the Ubuntu Software  Center should be OK after the upgrade.  Any you got from third party sites may need to be re-acquired.  Backup of course before any major upgrade, just in case.

---

### Post by QIII on 2015-10-28
Might I make the recommendation that you uninstall any proprietary drivers, particularly any proprietary video driver, prior to starting the upgrade?

One of the quickest ways to turn an upgrade into a significant emotional event is to fail to remove proprietary drivers.

---

### Post by javierdl on 2015-10-28
Mmmm, I'm so glad I asked!
Some apps were installed from the USC, but most with Synaptic, is that good too?
What about those installed with PPAs?
Those from a compressed file I'll have to re-install then.

JDL

---

### Post by QIII on 2015-10-28
USC, synaptic and from apt in the command line are good.  Those are all just different inerfaces for the same functions

Disable all of your PPAs and reinstall after upgrading.

---

### Post by grahammechanical on 2015-10-28
Applications put their user configuration files in the home folder. An upgrade will not remove those application folders. So, if you do need to re-install an application it will pick up the configuration files and load with the settings that it had before the upgrade.

Certain applications will also be upgraded in the process. Firefox, Libreoffice. The applications that get installed by default. An upgrade does not lose the configuration files. Applications that you have installed from compressed files will not be upgraded. But they will not be removed. They may not work after the upgrade.

Regards.

---

### Post by oldfred on 2015-10-29
As part of your normal backup you should include a list of ppa.

ls -l /etc/apt/sources.list.d/
```
fred@A105-Precise:~$ ls -l /etc/apt/sources.list.d/
total 40
-rw-r--r-- 1 root root 138 May 10 20:40 gwibber-daily-ppa-precise.list
-rw-r--r-- 1 root root 138 May 10 20:40 gwibber-daily-ppa-precise.list.save
-rw-r--r-- 1 root root 140 May 10 20:40 skunk-pepper-flash-precise.list
-rw-r--r-- 1 root root 140 May 10 20:40 skunk-pepper-flash-precise.list.save
-rw-r--r-- 1 root root 154 May 10 20:40 webupd8team-gvfs-libmtp-precise.list
-rw-r--r-- 1 root root 154 May 10 20:40 webupd8team-gvfs-libmtp-precise.list.save
-rw-r--r-- 1 root root 148 May 10 20:40 webupd8team-unstable-precise.list
-rw-r--r-- 1 root root 148 May 10 20:40 webupd8team-unstable-precise.list.save
-rw-r--r-- 1 root root 148 May 10 20:40 yannubuntu-boot-repair-precise.list
-rw-r--r-- 1 root root 148 May 10 20:40 yannubuntu-boot-repair-precise.list.save
```

But notice that I am running 12.04 precise on this system and all the ppa include precise in the ppa. If you upgrade you want the correct version for your new install. Also with a new install, you may not need a ppa as now that or similar software (often drivers) are included automatically, or the ppa is just obsoleted.

---

### Post by javierdl on 2015-10-29
GM, that's a relieve to know. Thanks for sharing :)

Fred, this command "[COLOR=#000000]ls -l /etc/apt/sources.list.d/[/COLOR]" aside of listing the PPAs, does it save them too? Or that's something you have to do manually?

---

### Post by oldfred on 2015-10-30
ls is just a listing. You need to copy to a file.

In my rsync back up file, I run several similar commands and add redirect to a folder in my /home so when I back up /home it is including the newest copy.

I have a long path to specific model system. but I just added the second line to my script as first just backs up current sources. If you upgrade of course sources will change. 
This is copied from my script and most commands in my script need sudo if run on their own. The ~ is /home/fred.

# So I know additional sources and ppas
cp /etc/apt/sources.list ~/Documents/LinuxDocs/CurrentSys/asus_ar/sources.list.backup
#ls -l /etc/apt/sources.list.d/
cp /etc/apt/sources.list.d ~/Documents/LinuxDocs/CurrentSys/asus_ar/sources.list.d.backup

 My backup includes this also. The dpkg list is a very long text list of all applications and the dependencies. You may want to edit it to remove obsolete, old kernels or others. It will not re-install anything already installed.

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

### Post by javierdl on 2015-10-30
Wow, thanks so much for the very complete reply. I'll have to read it a couple times to digest it well.

Happy Halloween! [IMG]https://ssl.gstatic.com/mail/emoji/5/48px/emoji_u1f47b.png[/IMG][IMG]https://ssl.gstatic.com/mail/emoji/5/48px/emoji_u1f383.png[/IMG]

---

