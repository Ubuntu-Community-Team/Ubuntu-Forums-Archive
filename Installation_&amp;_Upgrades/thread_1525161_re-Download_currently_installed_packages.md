---
title: "re-Download currently installed packages"
date: 2010-07-06
forum: Installation &amp; Upgrades
---

### Post by gsiliceo on 2010-07-06
Hi guys, i want to use apt-get or aptitude or whatever to re-download from the repositories the currently installed packages so i can move them to another pc without internet and dpkg install them there.
Any ideas how?

---

### Post by lechien73 on 2010-07-06
Maybe APTonCD is what you're looking for:

[http://sourceforge.net/projects/aptoncd/](http://sourceforge.net/projects/aptoncd/)

---

### Post by WinRiddance on 2010-07-06
The files from the repository change weekly, some of them even change daily. It wouldn't make sense to copy those files onto another drive. It would be next to impossible to have completely current data that way. The best solution is to create yourself a bootable ISO disk or USB stick when you need it. One of the "assumptions" that are made by Ubuntu developers is that you'll always have ready access to the internet in order to retrieve any needed updates immediately following the installation, and then as often as daily once the installation is finished.

This falls right in line with the fact that there's a new Ubuntu release every 6 months. So why would you want to copy the installation files somewhere else if those are going to change all of the time anyway?

If you want the files for backup purposes, to keep your system backed up and current at the same time, you might want to try something like the "Back in Time" backup utility which will permit you to make mirror images of your system which you can use later on to restore a system. With "Back in Time" you can even schedule to have those mirror images created weekly or monthly or whatever. Since Ubuntu uses the automatic update system you can always have a current updated image of everything on your hard disk. Those mirror images are very small too, much smaller than the actual data that you normally use. Here some links and a video for more information:

[http://www.youtube.com/watch?v=Tuu0OPuRP2k&feature=related](http://www.youtube.com/watch?v=Tuu0OPuRP2k&feature=related)

[http://backintime.le-web.org/](http://backintime.le-web.org/)

[http://www.ubuntugeek.com/back-in-time-a-simple-backup-tool-for-ubuntu.html](http://www.ubuntugeek.com/back-in-time-a-simple-backup-tool-for-ubuntu.html)

---

