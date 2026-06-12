---
title: "move most of  /home to new install of ubuntu"
date: 2011-10-06
forum: Installation &amp; Upgrades
---

### Post by blackbird34 on 2011-10-06
Hi everyone
I have had Ubuntu 10.10 then 11.04 installed on /dev/sda1 for the last six months, on a 58GB partition about half full, takes about a minute or so to start up, a little white cursor flaashes on and off before login screen for about 30 seconds. Does that mean it's loading a lot of stuff or what? 
On /dev/sda4 there is another (fresh) install of Natty, faster and cleaner with less clutter and files. If i move my documents and music etc on to the separate ( /dev/sda5) /home folder does it slow startup as much as my first Natty?
Most important I would like to transfer my whole firefox profile, my settings etc for libreoffice and my thunderbird profile with all the emails in it. How can i do this??
Thanks everyone!

---

### Post by blackbird34 on 2011-10-07
Please? how can i move my thunderbird profile, firefox profile and complete libreoffice settings over without making a horrible mess?

---

### Post by Lars Noodén on 2011-10-07
Look inside [FONT="Courier New"].mozilla[/FONT] and [FONT="Courier New"].mozilla-thunderbird[/font] for Firefox and Thunderbird profiles respectively.  LibreOffice's profile can be found in [FONT="Courier New"].libreoffice[/font]  Copy those directories to your new home and everything should be all set.

---

### Post by oldfred on 2011-10-08
Since I originally was sharing with XP, I moved my Thunderbird & Firefox profiles to a NTFS partition. I just edit my profile.ini in every new install and copy the entire profiles to my portable when we travel.

[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

If you have installed a lot of applications and want to keep them:
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

But you may want to edit list, it is just a text file. I was reinstalling python5 until I realized why. Now you may reinstall OpenOffice but the new version is LibreOffice and you do not want both.

---

### Post by blackbird34 on 2011-10-09
Thanks a lot. Firefox and Thunderbird worked perfectly. i'll keep that in mind...

Libreoffice didn't seem to work though. I use the autocomplete function a lot, especially, it didn't use prompt all the nice long complicated words that come up in french literature and history classes :P

---

