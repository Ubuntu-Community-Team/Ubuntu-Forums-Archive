---
title: "Can I upgrade from a 32-bit to a 64-bit system?"
date: 2014-08-14
forum: Installation &amp; Upgrades
---

### Post by kellyjmorris on 2014-08-14
I am presently using Ubuntu 12.04 LTS on a computer with a AMD FX-8120 Eight-Core Processor × 8 with 8 GB of SDRAM. I would like to use Update Manager to upgrade to Ubuntu 14.04.1 LTS. However, even though I have a 64-bit AMD processor, I discovered that I had installed a 32-bit version of the Ubuntu 12.04 LTS (why, I don't know ....).

If I use Update Manager to upgrade to 14.04.1, will I be able to install the 64-bit version of the OS (i.e. ubuntu-14.04.1-desktop-amd64 ), or will it default to installing the 32-bit version?

TIA

---

### Post by ian-weisser on 2014-08-14
> **kellyjmorris said:**
> If I use Update Manager to upgrade to 14.04.1, will I be able to install the 64-bit version of the OS (i.e. ubuntu-14.04.1-desktop-amd64 ), or will it default to installing the 32-bit version?

You cannot change between 32 and 64 using Update Manager. It's not an update. You must reinstall.

---

### Post by oldfred on 2014-08-15
You want to have really good backups which you should be doing anyway.

You want to include a list of installed apps, as if you have installed a lot it is easier just to reinstall from a list. You may also want to backup /etc if you had to manually edit any system settings like grub, wireless or other. But you may not want to just restore those as newer version may not need them or needs different ones.
And you want all of /home. If /home is a separate partition it becomes a lot easier as then you reuse that, but you should have it backed up anyway.

       Oldfred's list of stuff to backup May 2011:
[URL="http://ubuntuforums.org/showthread.php?t=1748541"]http://ubuntuforums.org/showthread.php?t=1748541
[/URL]
 Some files to exclude from /home backup - post #8 by  Paddy Landau
[URL="http://ubuntuforums.org/showthread.php?t=1883834"]http://ubuntuforums.org/showthread.php?t=1883834
      [/URL]
 More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

Of course if a server or server type install, you may have web or database apps in / (root) that should separately be backed up.


 from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

I have been using rsync to backup, but this looks like an ever better way.
 Sample rdiff file by TheFu
[http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880](http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880)
[http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use](http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use)



 
    [URL="http://ubuntuforums.org/showthread.php?t=1883834"]
[/URL]

[URL="http://ubuntuforums.org/showthread.php?t=1748541"]
[/URL]

---

