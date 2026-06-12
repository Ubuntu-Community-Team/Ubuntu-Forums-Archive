---
title: "trying to install make 3.81 on xubuntu - permission denied"
date: 2007-09-07
forum: Installation &amp; Upgrades
---

### Post by iam_what_iam on 2007-09-07
after un taring the tar.gz file, I attempted to ./INSTALL the INSTALL file, but when I typed that in (in the terminal) it responded by saying "permission denied."  I wondered if it was because I was not doing the installing as root so I changed to root, but the message "permission denied" once again returned when I tried a second time.

ultimately I am trying to get gtk installed, and am hoping to upgrade to the newest xfce window manager.  I am running dapper drake, and would really appreciate any help.  

So far i have not been able to get either gtk, or make installed.  
Thanks.

---

### Post by dickohead on 2007-09-07
have you tried:

sudo apt-get install build-essential

?

---

### Post by iam_what_iam on 2007-09-07
I just tried sudo apt-get install make

in terminal, and apparently "make is already newest version"

I don't get why when I'm trying to ./INSTALL i am getting "permission denied"

---

