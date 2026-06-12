---
title: "All attempts to upgrade 9.10 fail"
date: 2016-02-09
forum: Installation &amp; Upgrades
---

### Post by malfindin on 2016-02-09
So first you need to know I have to upgrade 9.10. I cannot install anything newer. ALL other newer distros simply fail to install. I have talked to many people and no one knows why. 9.10 installs and works fine. Except of course I need to update it as it's no longer supported.

I have tried every single way of upgrading it listed in: [https://help.ubuntu.com/community/EOLUpgrades/Karmic](https://help.ubuntu.com/community/EOLUpgrades/Karmic) 

Here's the main error I get:

frank@PVP-MAIN:~$ sudo do-release-upgrade -d
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading
extracting 'precise.tar.gz'
authenticate 'precise.tar.gz' against 'precise.tar.gz.gpg'
Traceback (most recent call last):
  File "/tmp/tmpyj6ndG/precise", line 3, in <module>
    from DistUpgradeMain import main
  File "/tmp/tmpyj6ndG/DistUpgradeMain.py", line 54, in <module>
    from DistUpgradeController import DistUpgradeController
  File "/tmp/tmpyj6ndG/DistUpgradeController.py", line 37, in <module>
    from utils import (country_mirror,
  File "/tmp/tmpyj6ndG/utils.py", line 28, in <module>
    apt_pkg.init_config()
AttributeError: 'module' object has no attribute 'init_config'

Please advise. I'm at my wits end.

---

### Post by matt_symes on 2016-02-09
Hi

> So first you need to know I have to upgrade 9.10. I cannot install anything newer. ALL other newer distros simply fail to install. I have talked to many people and no one knows why. 9.10 installs and works fine.

Is this just Ubuntu distos or others such as Fedora or Arch that fail to install ?

When it fails to install, what exactly fails ?

Kind regards

---

### Post by malfindin on 2016-02-09
I have only tried Ubuntu. You can see what I wrote about the errors in this thread: [http://ubuntuforums.org/showthread.php?t=2312953&p=13436516#post13436516](http://ubuntuforums.org/showthread.php?t=2312953&p=13436516#post13436516)

attempt to read or write outside of disk 'hd0'

Is the main error...

Basically. 9.10 installs and boots fine. Every single Ubuntu version 10.04 and later I get grub repair after rebooting after installing with no errors.

It's worth noting that originally I did upgrade Ubuntu 9.10 to 14.04 and it worked for a full year. Then a kernel update came in and I started getting the attempt to read or write outside of disk 'hd0' error. For a while I could use old kernel's to boot. When I tried to reinstall from scratch is when all install efforts began failing.

Nothing on this page works either: [http://askubuntu.com/questions/397485/what-to-do-when-i-get-an-attempt-to-read-or-write-outside-of-disk-hd0-error](http://askubuntu.com/questions/397485/what-to-do-when-i-get-an-attempt-to-read-or-write-outside-of-disk-hd0-error)

---

### Post by naxa on 2016-09-13
> **malfindin said:**
> 
  File "/tmp/tmpyj6ndG/utils.py", line 28, in <module>
    apt_pkg.init_config()
AttributeError: 'module' object has no attribute 'init_config'

Please advise. I'm at my wits end.

you can download the alternate cd from here:
[http://old-releases.ubuntu.com/releases/lucid/](http://old-releases.ubuntu.com/releases/lucid/)
mount it with eg. the following command (from a gnome-terminal program which you can start with Alt+F2):
    sudo mount -o loop ubuntu-10.04.4-alternate-i386.iso /media/cdrom0
then use the installer/upgrader on the cd:
    /media/cdrom0/cdromupgrade
choose NOT to use the internet / NOT to use newer packages. Then it will just use the CD.

Similar description is found here: [https://help.ubuntu.com/community/PreciseUpgrades#Upgrading_Using_the_Alternate_CD.2FDVD](https://help.ubuntu.com/community/PreciseUpgrades#Upgrading_Using_the_Alternate_CD.2FDVD)

---

