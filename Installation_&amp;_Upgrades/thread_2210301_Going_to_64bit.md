---
title: "Going to 64bit"
date: 2014-03-10
forum: Installation &amp; Upgrades
---

### Post by Windoze Refugee on 2014-03-10
HI Folks, 
I've been running ubuntu for a few years now, but always in 32 bit.
I have the hardware now to make the jump but want some advice about how best to do it.
I'm thinking of doing a clean install on a new HD and Ubuntu 64 bit, but IM a little concerned about how I then get all my files and settings across from the old (ie current) version in 32bit on an entirely separate HD.
Any suggestions?
Cheers
WR

---

### Post by ibjsb4 on 2014-03-10
For your personal files you could start using a [data partition]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=data+partition&sa=Search&cof=FORID:9").

---

### Post by oldfred on 2014-03-10
I converted to 64 bit with a new drive back with 9.10. But now my backup procedure is just the same as you need as I do not back up system assuming I will just do new install, but backup data & some configuration settings.

Most important is /home. Perhaps some settings in /etc and a list of installed apps, to make it easy to reinstall the 64 bit versions.

       Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Some files to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
 from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages


With some of my new installs I have had to cheat and go back into old install to find a setting or something, so I install into new / (root) partitions now, keeping old install for a while.

---

### Post by Windoze Refugee on 2014-03-21
Hi Guys.
Thanks for the input.
Ive made the switch and now have only to import all my old Thunderbird data..
&#8230;"only"&#8230;.
This is proving a far larger hurdle than I anticipated.
I've tried the import command in t-bird, but at the critical moment i.e. when it asks from whence to import I'm, offered no options . Arghhhhh
Anyone have any ideas?

---

### Post by oldfred on 2014-03-23
If you copied /home your Thunderbird profile still is in your /home.

I typically move my Thunderbird to another partition and share it with all my installs. But then I have to start Thunderbird to get it to create a new profile.ini and then edit profile.ini with my old profile location & name.

Info on profiles:
[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

---

