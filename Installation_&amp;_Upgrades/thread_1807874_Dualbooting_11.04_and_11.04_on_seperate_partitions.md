---
title: "Dualbooting 11.04 and 11.04 on seperate partitions"
date: 2011-07-19
forum: Installation &amp; Upgrades
---

### Post by Morrowdays on 2011-07-19
I have a question, I am dualbooting Nattynarwhal and Lucidlynx, however, I am interested in upgrade LL to NN. Both share separate homes and are on seperate partitions. Will there be any conflict?
Also would it be possible to install gnome3/shell on one of the distros without affected unity on the other partition?

---

### Post by MAFoElffen on 2011-07-19
> **Morrowdays said:**
> I have a question, I am dualbooting Nattynarwhal and Lucidlynx, however, I am interested in upgrade LL to NN. Both share separate homes and are on seperate partitions. Will there be any conflict?
Also would it be possible to install gnome3/shell on one of the distros without affected unity on the other partition?
Yes on both questions.  Past experience with that shows me it is painless and the os_prober is not confused by it.  Although- I have to keep it straigt in "my head" which menu item was which.

---

### Post by Morrowdays on 2011-07-19
Is there any possibility of renaming the lines on Grub bootloader so that won't be a problem?

---

### Post by MAFoElffen on 2011-07-19
> **Morrowdays said:**
> Is there any possibility of renaming the lines on Grub bootloader so that won't be a problem?
You can edit /boot/grub/grub.cfg with root privileges to do that... but it will get overwritten each time it updates... or add one as a dupe/alternate in /etc/grub.d/40_custom.

---

### Post by oldfred on 2011-07-19
Have you installed a lot of applications and would want to reinstall the same ones?

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

You can edit some things in grub with this:
HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
The Grub 2 Guide (formerly Grub 2 Basics) manual way
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

