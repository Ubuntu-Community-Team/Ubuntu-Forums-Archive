---
title: "finding dependencies and installing application without internet at all"
date: 2010-01-22
forum: Installation &amp; Upgrades
---

### Post by joamon on 2010-01-22
Hi,
I am new user to linux and i am seriously thinking to move to linux from windows,
i am trying ubuntu 9.10 and 8.04 and my major problem is i DO NOT have INTERNET connection.(I really do not know whether this is a question that is already repeated.)
i want to know how to find out the necessary dependencies for an application to work and make a list and download it from some other computer having internet and install it on my home computer,
i have searched the web intensively and could not find a correct solution for this ,
IS their a solution for this ?
I found this command sudo apt-get --print-uris --yes install vlc | grep ^\' | cut -d\' -f2 >mydownload.txt
WHICH requires internet .
is their a really better option than this ?
Please let me know :confused:

---

### Post by MelDJ on 2010-01-22
hi, 
see [https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

---

### Post by ankspo71 on 2010-01-22
Hi,
[http://keryxproject.org/](http://keryxproject.org/)      Windows and Linux
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)    Linux only

Either of those two programs can be installed on a computer with an internet connection, and are used to download all of the required packages for any software you want from the repositories, so that you can put the packages on a cd and install them on another computer that does not have internet.

Have you tried inserting your Ubuntu cds into your drive, then go to System > Administration, Software Sources.... then click on the Other Software tab, and select the cd as a place to download from?

I think when I insert my cd, a prompt comes up asking me if I want to "start package manager". That's something else to try too.

Hope these ideas help.

---

