---
title: "How to upgrade 8.04.1 to 8.10 ?"
date: 2008-10-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by gregphil on 2008-10-05
If ubuntu 8.04.1 is already installed and running (from Live! DVD) what is the easy way to try out or "upgrade" to 8.10 beta?  Is there a Live Cd or DVD yet?
 
Can I keep all the settings from 8.04.1 through the upgrade?
 
Thank You.
 
P.S.  Same question for kubuntu 8.04.1  (installed on a separate disk).  Is kubuntu 8.10 basicly the same as kubuntu alternate updated to KDE 4.1.1?

---

### Post by bobnutfield on 2008-10-05
> **gregphil said:**
> If ubuntu 8.04.1 is already installed and running (from Live! DVD) what is the easy way to try out or "upgrade" to 8.10 beta?  Is there a Live Cd or DVD yet?
 
Can I keep all the settings from 8.04.1 through the upgrade?
 
Thank You.
 
P.S.  Same question for kubuntu 8.04.1  (installed on a separate disk).  Is kubuntu 8.10 basicly the same as kubuntu alternate updated to KDE 4.1.1?

Are you saying the you installed FROM the LIVE CD or that you are RUNNING the LIVE CD?  If you have Hardy installed to your hard drive you will be given the opportunity to upgrade when Intrepid is released.  It is now in Beta, but you can download the Beta Live CD, but there is still some bugs.

---

### Post by halitech on 2008-10-05
from what I know, you can't use the Live CDs to upgrade, only the alternate cds or by doing it through the update manager. The settings *should* stay but as always, backup before upgrading.

---

### Post by gregphil on 2008-10-05
Where can I find a link for downloading the Live! CD for ubuntu 8.10 or kubuntu 8.10?
 
I am in North America (Seattle, Washington, USA)
 
Thank You.

---

### Post by halitech on 2008-10-05
[http://www.ubuntu.com/](http://www.ubuntu.com/)

---

### Post by bobnutfield on 2008-10-05
[http://ftp.ucsb.edu/pub/mirrors/linux/ubuntu/8.10/ubuntu-8.10-beta-desktop-i386.iso]("http://ftp.ucsb.edu/pub/mirrors/linux/ubuntu/8.10/ubuntu-8.10-beta-desktop-i386.iso")

---

### Post by Delvien on 2008-10-05
```
 sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by kindofabuzz on 2008-10-05
To update from Hardy:
```
update-manager -d
```

---

### Post by wgrant on 2008-10-05
> **Delvien said:**
> ```
 sudo apt-get update && sudo apt-get dist-upgrade
```

No. That hasn't been supported for years. Don't do it.

---

### Post by Sef on 2008-10-05
> To update from Hardy:
 	Code:
 	update-manager -d 


For a more detailed how to update, see this [sticky]("http://ubuntuforums.org/showthread.php?t=936696").

---

### Post by talkingwires on 2008-10-06
> **wgrant said:**
> No. That hasn't been supported for years. Don't do it.Really? Because I've been doing it for years. I've got a system I upgraded from the Warty betas all the way up to Hardy before I wiped the HDD, and never had a problem dist-upgrading...

---

### Post by The Keeper on 2008-10-06
> **wgrant said:**
> No. That hasn't been supported for years. Don't do it.

Say what? Do you mean the update manager is the only supported method of upgrading? What of command line-only setups of Ubuntu?

---

### Post by davidyu on 2008-10-06
I upgrade 8.10 Beta from 8.04 last weekend via update-manager -d
Unfortunately, After reboot, the result is bad. Only see Ubuntu wallpaper without login input. I reboot many times, got the same bad result.  At last, I need to burn a 8.10 Beta CD and reinstall 8.10 Beat from scratch.
   Sorry, this is bad story.

---

### Post by MaX on 2008-10-06
This isn't Windows, stuff don't fix itself by rebooting.... If it's broken it's broken.

I suspect you upgraded the wrong day. You should have switched to a terminal and updated packages the next day to see if stuff got fixed.

---

### Post by Sef on 2008-10-06
> I upgrade 8.10 Beta from 8.04 last weekend via update-manager -d
Unfortunately, After reboot, the result is bad. Only see Ubuntu wallpaper without login input. I reboot many times, got the same bad result. At last, I need to burn a 8.10 Beta CD and reinstall 8.10 Beat from scratch.
   Sorry, this is bad story.

That is ok your story is not a happy one.  Without people saying what is wrong, Ubuntu could never fix as many bugs as it does.   A clean install is the best way to install.  It has less problems than an update.

---

### Post by Archmage on 2008-10-06
> **davidyu said:**
> I upgrade 8.10 Beta from 8.04 last weekend via update-manager -d
Unfortunately, After reboot, the result is bad. Only see Ubuntu wallpaper without login input. I reboot many times, got the same bad result.

I got the same problem with my nVidia-card. I need to change on line in the config and now everything is working.

---

### Post by wgrant on 2008-10-06
> **The Keeper said:**
> Say what? Do you mean the update manager is the only supported method of upgrading? What of command line-only setups of Ubuntu?

Yes. do-release-upgrade is used if one doesn't use X.

---

### Post by The Keeper on 2008-10-06
> **wgrant said:**
> Yes. do-release-upgrade is used if one doesn't use X.

First time I've even heard of it.

Why apt-get isn't supported anymore? What does do-release-upgrade do that apt-get can't?

---

### Post by ssam on 2008-10-06
you should read the release notes and upgrade notes.

the 8.04 upgrade notes describe all the upgrade methods
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

the upgrade script does a few extra things than apt to help the upgrade go smoothly.
* checks that there is enough disk space
* updates sources.list
* disables 3rd party repos
* makes sure the right meta packages are installed
* makes sure new packages get installed and gets rid of old packages (good for package transitions)

---

### Post by wgrant on 2008-10-06
> **ssam said:**
> you should read the release notes and upgrade notes.

the 8.04 upgrade notes describe all the upgrade methods
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

the upgrade script does a few extra things than apt to help the upgrade go smoothly.
* checks that there is enough disk space
* updates sources.list
* disables 3rd party repos
* makes sure the right meta packages are installed
* makes sure new packages get installed and gets rid of old packages (good for package transitions)

It will also handle upgrade special cases (particularly X driver and configuration migrations). There's no reason not to use it.

---

### Post by Delvien on 2008-10-06
> **wgrant said:**
> Yes. do-release-upgrade is used if one doesn't use X.

That's weird, and doesn't make sense. Who made that decision lol!

---

### Post by wgrant on 2008-10-06
> **Delvien said:**
> That's weird, and doesn't make sense. Who made that decision lol!

What doesn't make sense lol?

---

### Post by Hobbsee on 2008-10-06
> **Delvien said:**
> That's weird, and doesn't make sense. Who made that decision lol!

On the contrary.  One of the things it handles is X changes.  There are other things it handles, with it's package hints, too, which are not restricted to a GUI.

---

### Post by The Keeper on 2008-10-07
Is apt-get upgrade still supported for keeping Ubuntu up-to-date, or should Update Manager be used instead? If apt-get isn't supported, what is cli alternative of Update Manager?

---

### Post by wgrant on 2008-10-07
> **The Keeper said:**
> Is apt-get upgrade still supported for keeping Ubuntu up-to-date, or should Update Manager be used instead? If apt-get isn't supported, what is cli alternative of Update Manager?

apt-get is fine within a release. But not between releases.

---

