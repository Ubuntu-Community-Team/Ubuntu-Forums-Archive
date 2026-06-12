---
title: "Want to upgrade but afraid of crashes"
date: 2011-10-05
forum: Installation &amp; Upgrades
---

### Post by EthioJOB on 2011-10-05
I have Ubuntu 10.10 installed on my PC (dual boot with Windows 7) and I was thinking about upgrading to 11.04. However, I'm afraid that my system might potentially crash as I have a number of applications -  more than 10 - installed on my system and made some minor tweaks (changed resolution, placed window buttons on the right, did some tinkering to fix the sound, etc). I thought of some ideas:-

1. Put Natty on a USB flash drive, take that drive somewhere with an internet and install the same applications on it (with the natty supported versions of course), and take the Live USB back home and upgrade the system with it. Just an idea, have no idea of how good or bad it is.

2. Uninstall all or most software and upgrade to Natty, then reinstall the applications. Sounds safe, but that would be cumbersome.

3. Just go with it. Risky, but ...

Any thoughts would be appreciated. 

BTW I don't have an internet connection at my home; I use internet elsewhere for downloading and stuff. So if you have any suggestions please take this into consideration.

Thanks

---

### Post by dino99 on 2011-10-05
if you have made the installation with a separate /home, then your data/settings are safe.

you can easily test a newer distro/release via virtualbox installed on the actual 10.10. then if you have a good feeling with the new release after a while, upgrading will bring less fear :)

---

### Post by kurt18947 on 2011-10-05
At this point, you might want to just wait for 11.10 to be released for a while -- perhaps a month -- then try it as a Live CD or Live USB device and see how your hardware likes it.  Many here say that Unity works much better in 11.10 than it does in 11.04 if that matters to you. 11.10 also has available Gnome 3 & gnome-shell whereas 11.04 is still Gnome 2.32 as the Unity alternative.

---

### Post by Frogs Hair on 2011-10-05
I would wait for 11.10 backup or create a home partition and do a clean installation . If you choose to upgrade now purge any PPA's and remove the proprietary graphics driver if in use . If you are downloading in another location , make sure that there are no download limitations . Upgrade or ISO downloads are fairly large , so internet speed and download size may come into play at a certain locations .

---

### Post by oldfred on 2011-10-05
I have not used any of these, but saved links:

aptoncd 
[https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD)
Download once for many machines
How To Install Apt-Cacher-NG in Ubuntu Linux
[http://ubuntuforums.org/showthread.php?t=981085](http://ubuntuforums.org/showthread.php?t=981085)
Location of downloaded debs
/var/cache/apt/archives/
sudo apt-get install --no-download <package name>

I do use this to know all the packages I have installed. When I do a new install I use this list to reinstall. It only downloads the packages not already installed by the installCD/USB. And it installs the newer version if one. I have had very old packages not get installed. And some should be manually edited like OpenOffice is now LibreOffice so you do not want both. Not sure if there is a way to combine this with aptoncd.

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

### Post by EthioJOB on 2011-10-06
I can't uprade to 11.10 without going through 11.04 first. The OS wouldn't allow so. A clean install (after a cumbersome data backing) sounds like a viable option, but I've got Windows 7 installed and I don't want any complications there (the bootloader may cause trouble).

@oldfred
I'll go through the threads you posted when I get the time and will repost.

---

