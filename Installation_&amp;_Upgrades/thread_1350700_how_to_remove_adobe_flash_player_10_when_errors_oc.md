---
title: "how to remove adobe flash player 10 when errors occur on the way?"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by bizar on 2009-12-09
Hello people :p
I would like to ask you for a bit of help.
I recently tried to install the new adobe flash player 10, but everythig backfired, because, from what I have understood, the install package was broken, and now, I don't know why, I can't install or uninstall anything, because packages are brocken, and the system can't find the archive of the adobe flash player.
there is a red dot with a white line in the bar, and when I select it it says:

[SIZE=2]*"An error occurred, please run Package Manager fom the right-click menu or apt-get in a terminal to see what is wrong.The error message was: ' Unknown Error:'<type 'exceptions.SystemError'> (E:The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.)' This usually means that your installed packages have unmet dependencies."*[/SIZE]
[SIZE=1]
I click it and than the update manager starts and tells me that "[SIZE=2]*not all updates can be installed"*[SIZE=1] and than I click "partial upgrade" then, it asks me if I want to remove the package in bad state, I choose yes, package begins to upgrade, then suddently it stops and an error message appears and says:

"[SIZE=3]Package in inconsistent state"
[SIZE=1]so, it doesen't work. 
[SIZE=4]

please if you have any ideas what I should do, type it :D
thanks :) ([SIZE=2]btw, I use ubuntu version 9.10[/SIZE])
[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]

---

### Post by phillw on 2009-12-09
> **bizar said:**
> Hello people :p
I would like to ask you for a bit of help.
I recently tried to install the new adobe flash player 10, but everythig backfired, because, from what I have understood, the install package was broken, and now, I don't know why, I can't install or uninstall anything, because packages are brocken, and the system can't find the archive of the adobe flash player.
there is a red dot with a white line in the bar, and when I select it it says:

[SIZE=2]*"An error occurred, please run Package Manager fom the right-click menu or apt-get in a terminal to see what is wrong.The error message was: ' Unknown Error:'<type 'exceptions.SystemError'> (E:The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.)' This usually means that your installed packages have unmet dependencies."*[/SIZE]
[SIZE=1]
I click it and than the update manager starts and tells me that "[SIZE=2]*not all updates can be installed"*[SIZE=1] and than I click "partial upgrade" then, it asks me if I want to remove the package in bad state, I choose yes, package begins to upgrade, then suddently it stops and an error message appears and says:

"[SIZE=3]Package in inconsistent state"
[SIZE=1]so, it doesen't work. 
[SIZE=4]

please if you have any ideas what I should do, type it :D
thanks :) ([SIZE=2]btw, I use ubuntu version 9.10[/SIZE])
[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]


Sorry for the delay - I didn't have the thread bookmarked ....

> Hi try this first ..     
     ```
sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm
sudo dpkg-reconfigure adobe-flashplugin --force
sudo dpkg --purge --force-all adobe-flashplugin 
```
If that fails, then head over to [http://ubuntuforums.org/showthread.php?t=1305829&page=3](http://ubuntuforums.org/showthread.php?t=1305829&page=3) 
and follow the longer set of instructions.

Regards,

Phill.

---

