---
title: "Failed to update ubuntu 17.10. The repository does not have a Release file."
date: 2018-01-18
forum: Installation &amp; Upgrades
---

### Post by mauimail on 2018-01-18
I have been using 17.10 for a bit now and have had very little trouble. All of the sudden I am getting issues updating. I have seen posts about this same issue in reference to repositories that are not supported by Ubuntu, but from what I can tell it is the Ubuntu repositories that I am having the issue with. When I run  sudo apt-get update through the terminal I get the following output:

---------------------------------------------------------------------------------------------------------------
```

Hit:1 http://archive.canonical.com/ubuntu xenial InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu artful InRelease                     
Ign:3 http://dl.google.com/linux/chrome/deb stable InRelease                   
Hit:4 http://us.archive.ubuntu.com/ubuntu artful-updates InRelease             
Hit:5 http://dl.google.com/linux/chrome/deb stable Release                     
Hit:6 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease             
Ign:7 http://archive.ubuntu.com/ubuntu zesty InRelease                         
Ign:8 http://security.ubuntu.com/ubuntu zesty-security InRelease        
Hit:9 http://us.archive.ubuntu.com/ubuntu artful-backports InRelease    
Hit:10 http://us.archive.ubuntu.com/ubuntu artful-security InRelease           
Ign:11 http://archive.ubuntu.com/ubuntu zesty-updates InRelease                
Err:12 http://security.ubuntu.com/ubuntu zesty-security Release          
  404  Not Found [IP: 2001:67c:1560:8001::14 80]
Err:14 http://archive.ubuntu.com/ubuntu zesty Release
  404  Not Found [IP: 2001:67c:1560:8001::11 80]
Err:15 http://archive.ubuntu.com/ubuntu zesty-updates Release
  404  Not Found [IP: 2001:67c:1560:8001::11 80]
Reading package lists... Done
E: The repository 'http://security.ubuntu.com/ubuntu zesty-security Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu zesty Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu zesty-updates Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```



----------------------------------------------------------------------------------------------------------------

I have also found something strange through using tips from solved threads that may be part of this issue. When I use the GUI System Settings > Software and Updates > Download from... and then reload the repository information, I get a "Failed to download repository information; Check your internet connection" error for any server I choose, even the "best" server option. Obviously my internet connection is working as I am using the same machine to write this thread. Any guidance in this matter would be greatly appreciated. Cheers.

---

### Post by Impavidus on 2018-01-18
You've mixed software sources for 3 different releases of Ubuntu: 16.04, 17.04 and 17.10. This is a bad idea, generally. The error message is caused by the sources for 17.04, which reached end of life. Remove all sources for releases other than 17.10 "artful" from your /etc/apt/sources.list.

---

### Post by mauimail on 2018-01-31
Hmmmm. When I navigate through the terminal to cd /etc/apt/sources.list.d (which is the only dir that resembles the above mentioned dir) there are only 3 google chrome sources. Nothing at all in any of the other dir's in apt either. and when I use the GUI, no previous sources are checked on the checklist. Not really sure where else to look...

---

### Post by cruzer001 on 2018-01-31
You need to drop the ".d"
```

sudo nano /etc/apt/sources.list  ##or cd into it if you wish
```

[https://www.nano-editor.org/dist/v2.2/nano.html](https://www.nano-editor.org/dist/v2.2/nano.html)

Also a good idea to make a backup copy first.

---

### Post by mauimail on 2018-02-02
Excellent! This got me there. Not sure why i missed this the first time, but no matter. I really appreciate you guys. I know Impavidus suggested removing all non-"artful" sources. Would you guys recommend commenting the lines out or deleting the lines altogether? After making a backup copy of course...

---

### Post by cruzer001 on 2018-02-02
If you just comment out; a mistake is easy to correct.  You can later clean it up if you wish.  Like you said, leave only "artful".

And yes, do make a backup.
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.old
```

That should do it

---

### Post by Impavidus on 2018-02-02
@mauimail: Don't disable the google repositories. That's where updates to chrome come from.

---

### Post by mauimail on 2018-02-02
I’ll make those changes tonight, and if all is well I’ll update and mark this thread as Solved.

---

### Post by cruzer001 on 2018-02-02
> **Impavidus said:**
> @mauimail: Don't disable the google repositories. That's where updates to chrome come from.

Missed that, good catch.

And if you do run into a snag, post your sources for us to have a look.

```
cat /etc/apt/sources.list
```

---

### Post by mauimail on 2018-02-02
Thanks guys. This did the trick. I'll post my source lists (old and new) just for future reference so anyone who needs this fix in the future can follow better. I don't know if it's actually worth it or not, but I always like to find detailed fixes in these forums so here it is. Btw, my chrome sources are in a script in that sources.list.d dir, not the sources.list script. I'm not sure if that makes any difference or not. Chrome seems to update just fine. 

Original sources.list that was giving me trouble:
-----------------------------------------------------------------------------------------------------------------------------------------

```
# deb cdrom:[Ubuntu 17.04 _Zesty Zapus_ - Release amd64 (20170412)]/ zesty main restricted
# deb cdrom:[Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)]/ xenial main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ artful main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ artful-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ artful universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial universe
deb http://us.archive.ubuntu.com/ubuntu/ artful-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ artful multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://us.archive.ubuntu.com/ubuntu/ artful-updates multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ artful-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu xenial partner
# deb-src http://archive.canonical.com/ubuntu xenial partner


deb http://us.archive.ubuntu.com/ubuntu/ artful-security main restricted
# deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ artful-security universe
# deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://us.archive.ubuntu.com/ubuntu/ artful-security multiverse
# deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
# deb-src http://us.archive.ubuntu.com/ubuntu/ zesty main restricted


## Major bug fix updates produced after the final release of the
## distribution.
# deb-src http://us.archive.ubuntu.com/ubuntu/ zesty-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ zesty universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ zesty-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ zesty multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ zesty-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ zesty-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu zesty partner
# deb-src http://archive.canonical.com/ubuntu zesty partner


# deb-src http://security.ubuntu.com/ubuntu zesty-security main restricted
# deb-src http://security.ubuntu.com/ubuntu zesty-security universe
# deb-src http://security.ubuntu.com/ubuntu zesty-security multiverse
# deb http://mkvtoolnix.download/ubuntu/zesty/ ./ # disabled on upgrade to artful
# deb-src http://mkvtoolnix.download/ubuntu/zesty/ ./ # disabled on upgrade to artful
deb http://archive.ubuntu.com/ubuntu zesty main universe restricted
deb http://security.ubuntu.com/ubuntu/ zesty-security universe restricted main
deb http://archive.ubuntu.com/ubuntu zesty-updates universe restricted main
```
==============================================================================

Edited sources.list script:
----------------------------------------------------------------------------------------------------------------------------------------
```
# deb cdrom:[Ubuntu 17.04 _Zesty Zapus_ - Release amd64 (20170412)]/ zesty main restricted
# deb cdrom:[Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)]/ xenial main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ artful main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ artful-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ artful universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial universe
deb http://us.archive.ubuntu.com/ubuntu/ artful-updates universe
#deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ artful multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://us.archive.ubuntu.com/ubuntu/ artful-updates multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ artful-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
#deb http://archive.canonical.com/ubuntu xenial partner
# deb-src http://archive.canonical.com/ubuntu xenial partner


deb http://us.archive.ubuntu.com/ubuntu/ artful-security main restricted
# deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ artful-security universe
# deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://us.archive.ubuntu.com/ubuntu/ artful-security multiverse
# deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
# deb-src http://us.archive.ubuntu.com/ubuntu/ zesty main restricted


## Major bug fix updates produced after the final release of the
## distribution.
# deb-src http://us.archive.ubuntu.com/ubuntu/ zesty-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ zesty universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ zesty-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ zesty multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ zesty-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ zesty-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu zesty partner
# deb-src http://archive.canonical.com/ubuntu zesty partner


# deb-src http://security.ubuntu.com/ubuntu zesty-security main restricted
# deb-src http://security.ubuntu.com/ubuntu zesty-security universe
# deb-src http://security.ubuntu.com/ubuntu zesty-security multiverse
# deb http://mkvtoolnix.download/ubuntu/zesty/ ./ # disabled on upgrade to artful
# deb-src http://mkvtoolnix.download/ubuntu/zesty/ ./ # disabled on upgrade to artful
#deb http://archive.ubuntu.com/ubuntu zesty main universe restricted
#deb http://security.ubuntu.com/ubuntu/ zesty-security universe restricted main
#deb http://archive.ubuntu.com/ubuntu zesty-updates universe restricted main
```
============================================================================

---

### Post by mauimail on 2018-02-02
Figured out how to use those code boxes too. =d>

---

### Post by cruzer001 on 2018-02-03
Welcome :)

---

### Post by mwilliams1220 on 2018-04-21
Thanks! This was exactly what I was looking for!

---

