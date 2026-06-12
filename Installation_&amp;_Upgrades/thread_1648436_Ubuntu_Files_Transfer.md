---
title: "Ubuntu Files Transfer"
date: 2010-12-18
forum: Installation &amp; Upgrades
---

### Post by volamoot on 2010-12-18
Hello,

I'm not entirely sure if what I'm wondering if possible, but i'll try to explain it as best I can. I recently bought a new laptop, and I'm about to install Ubuntu 10.10 Desktop Edition onto it. I have been using Ubuntu 10.10 on a desktop, and I am trying to find a way to just transfer all the files and settings over to the laptop while still leaving the files intact on the desktop.

Please Help.

---

### Post by oldfred on 2010-12-18
I did this, but do not remember all the details.

I had Ubuntu on my desktop and windows on laptop and was copying files with Samba. But it seemed every update to windows or firewall and sometimes changes to Ubuntu made me reset Samba. So I just installed Ubuntu onto my portable and converted to NFS.

I did not attempt to copy most /home settings over. But I have two data partitions one NTFS left from when I was dual booting a lot and one exxt3. I set up the same partitions in my portable. My NTFS partition also has my Firefox & Thunderbird profiles.

I did export a list of all installed applications and set up a script to set up system as best as I could automatically and reinstall apps. Then I only have a few manual changes to make.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

 dpkg --get-selections > ubuntu-files
From my history to reinstall - I rename ubuntu-files with current date and whether from portable or desktop.
  431  dpkg --set-selections < ubuntu-filesport2010Mar
  432  sudo dpkg --set-selections < ubuntu-filesport2010Mar
  434  sudo apt-get -y update
  435  sudo apt-get update
  436  sudo apt-get dselect-upgrade
  437  history


HOWTO: NFS Server/Client if no windows 
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by volamoot on 2010-12-21
Thanks! That did the trick. I was able to transfer the majority of my files and settings. the settings and files i couldn't get to transfer ended up just being put onto a flash drive and transfered that way. Thanks again!

---

