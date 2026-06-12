---
title: "Upgrading from 11.10 to 14.04"
date: 2014-08-21
forum: Installation &amp; Upgrades
---

### Post by kiwipenguin on 2014-08-21
Hi, just wondering the safest way to upgrade my laptop from 11.10 to 14.04.
I have backed up the home folder and made a list of packages that I have installed (in a text file).
Now I think I am ready to update.

I need to do the process over the internet as there is no way of connecting an external disk drive or usb device.

The reason I am asking this question is that I went through hours and days of trying to fix little problems when I installed 11.10 back in the day, and I would prefer not to have to repeat this. I had to find fixes that would mute the speakers when plugging in headphones, or increase the brightness of the skype camera, or get thunderbird to open in the background when starting up, etc, etc...

I have googled around but not yet found the answer.
Does anybody know if there are any instructions out there for upgrading to a new version of ubuntu without losing all the uniique changes and tweaks necessary for each type of machine?

Thanks!

---

### Post by yancek on 2014-08-21
There really isn't any 'safe' way although I have always had good luck doing it.  Back up any important data first.  You might give the link below a read as it explains exactly what you want, upgrading 11.10 to 12.04 which you must do before you can upgrade to 14.04.  I haven't used this page so read carefully.  This is one of the best reasons for using an LTS release.

[http://www.howtoforge.com/how-to-upgrade-ubuntu-11.10-oneiric-ocelot-to-12.04-lts-precise-pangolin-desktop-and-server](http://www.howtoforge.com/how-to-upgrade-ubuntu-11.10-oneiric-ocelot-to-12.04-lts-precise-pangolin-desktop-and-server)

The site below is at the Ubuntu site and might be better.

[https://help.ubuntu.com/community/PreciseUpgrades](https://help.ubuntu.com/community/PreciseUpgrades)

---

### Post by oldfred on 2014-08-21
If you did make hardware setting changes those may be in /etc. I might back that up also, but not necessarily just restore that. New version may not need all the settings or some may not work the same. But good to have the reference.

       Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

 More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
      
 Some files to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

 from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

---

### Post by mastablasta on 2014-08-21
upgrade rewrites most if not all of the tweaks. the question is if these tweaks will even be necessary when using newer kernel.

upgrade or not less stuff worked when I went to 14.04 and I had to do new tweaks. but at least I can use it for 5 years now before I need to upgrade anything. and by that time I will need windows 9 or 10 or whatever on the other side of the disk anyway....

---

### Post by grahammechanical on 2014-08-21
There is a certain similarity to the look of Ubuntu 14.04 with that of Ubuntu 11.10 but underneath the difference is greater then the difference in look between Ubuntu 11.10 and Ubuntu 10.10. There is also a big difference in underlying code between Ubuntu 14.04 and 12.04. To get to the end of this process with a working system will be an achievement in itself. Do not expect more than that. You tell us if it is successful. 

Me? I would be doing a fresh install.

---

