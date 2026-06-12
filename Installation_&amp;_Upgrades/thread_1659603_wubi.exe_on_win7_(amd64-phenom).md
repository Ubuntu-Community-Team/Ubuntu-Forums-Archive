---
title: "wubi.exe on win7 (amd64-phenom)"
date: 2011-01-04
forum: Installation &amp; Upgrades
---

### Post by pietb on 2011-01-04
Hi,
I'am trying to run 'wubi.exe' on my desktop(AMD phenom x4) running win7 premium.
ubuntu-10.10-desktop-i386.iso and wubi.exe (extracted from the *.iso file) are located in the same folder.
After launching wubi, there is some activity on my pc but the program doesn't continue, after a while I don't see any processor activity anymore, tried to run it as administrator with the same result. 
I did the same on my laptop (Intel core2 cpu)and there it went fine.
Is there somebody who can help? thanks in advance.

---

### Post by Frogs Hair on 2011-01-04
To check your download for corruption see the first link . For 23bit  and other instructions see the second link. To download Wubi .exe from the maverick index page see the third link (bottom of page) I think your download may be corrupt .  

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

[http://releases.ubuntu.com/maverick/](http://releases.ubuntu.com/maverick/) (Index)

---

### Post by bcbc on 2011-01-04
Go to the %temp% folder and delete the py*** directories and py**.exe files.

I saw a case before where wubi.exe didn't run and no log file was created. This fixed it. No explanation, but figure it's worth a shot ;)

Unless you actually find a wubi-10.10-rev197.log file in the %temp% directory - post that if you have it.

---

