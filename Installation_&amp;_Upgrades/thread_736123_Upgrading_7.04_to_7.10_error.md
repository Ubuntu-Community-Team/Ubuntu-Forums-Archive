---
title: "Upgrading 7.04 to 7.10 error"
date: 2008-03-26
forum: Installation &amp; Upgrades
---

### Post by razta on 2008-03-26
Hello,
Ive had Ubuntu 7.04 (feisty) installed on to my PC for about 2 days now, no problems at all, everything worked 'out of the box'.

I just got it on the net today and thought I would update everything, updated all the software packages fine but when I try and update ubuntu from 7.04 to 7.10 I got the following error:

> Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)

Im updating via the Update Manager, I tried a fix that was on the forums by unticking 2third party software" in add/remove but I still get the same error.

Any ideas on how to fix this? Im 2 days new to Linux so I havent a clue at this stage.

Thanks in advance.

---

### Post by Pumalite on 2008-03-26
Try changing your Server.

---

### Post by Twitch6000 on 2008-03-26
ok uncheck all those boxes in add/remove  it really helps,then try again if it fails restart the computer,then try it via terminal.
The code would be sudo apt-get update
then sudo apt-get upgrade

---

### Post by razta on 2008-03-26
> **Pumalite said:**
> Try changing your Server.

Ive got a wired connetion straight to the router.

---

### Post by Bölvaður on 2008-03-26
it is much more complicated to upgrade a whole system in one go with out having anything breaking down like this. The best way to avoid errors in my experience when moving from earlier releases is to burn the newest cd and install from scratch.

Btw. There is a new release in almost exactly one month which is a 'Long Term Service'. So you might want to fiddle with your Ubuntu like you want to have proper experience when you set up the longterm installation.

---

### Post by razta on 2008-03-26
> **Twitch6000 said:**
> ok uncheck all those boxes in add/remove  it really helps,then try again if it fails restart the computer,then try it via terminal.
The code would be sudo apt-get update
then sudo apt-get upgrade

Tried he above and get the following error;
```
ryan@ryan-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

> it is much more complicated to upgrade a whole system in one go with out having anything breaking down like this. The best way to avoid errors in my experience when moving from earlier releases is to burn the newest cd and install from scratch.

Btw. There is a new release in almost exactly one month which is a 'Long Term Service'. So you might want to fiddle with your Ubuntu like you want to have proper experience when you set up the longterm installation.

Think I might try this solution as I also have windowsXP installed on the same HDD which I want to delete so I can use the space for Ubuntu, would be easier to do the lot at once.

Thank you all for your help/advice!

---

### Post by bapoumba on 2008-03-27
In the first post, the repos are for feisty.
Please paste your sources.list:
```
cat /etc/apt/sources.list
```

---

