---
title: "Version Help"
date: 2010-06-28
forum: Installation &amp; Upgrades
---

### Post by joelw135 on 2010-06-28
This afternoon I ran the command "update-manager -d" and version 10.10 was available. I ran the install and everything went smoothly and old files were deleted and the computer restarted. I logged in with no errors. When I went to about Ubuntu it still said 10.4 how do I check to see if it actually upgraded to Maverick?

 I ran this in terminal cat /etc/issue and it shows Mavrick. Why does About Ubuntu show wrong and how do I fix it?

---

### Post by arpanaut on 2010-06-28
I hope that you realize that Maverick is at alpha 1 stage of development, Daily updates can and will break you installation.

[http://ubuntuforums.org/forumdisplay.php?s=&daysprune=&f=385](http://ubuntuforums.org/forumdisplay.php?s=&daysprune=&f=385)

is where you need to be asking questions about Developmental Releases, Please read the stickies, in that forum and be prepared for any eventuality.  i.e. have backups of your improtant data!

I hope this is not your primary daily runner OS installation.

P.S. First and foremost while testing developmental releases do not blindly accept "partial updates"!  Read appropriate sticky.

---

### Post by joelw135 on 2010-06-28
> **arpanaut said:**
> I hope that you realize that Maverick is at alpha 1 stage of development, Daily updates can and will break you installation.

[http://ubuntuforums.org/forumdisplay.php?s=&daysprune=&f=385](http://ubuntuforums.org/forumdisplay.php?s=&daysprune=&f=385)

is where you need to be asking questions about Developmental Releases, Please read the stickies, in that forum and be prepared for any eventuality.  i.e. have backups of your improtant data!

I hope this is not your primary daily runner OS installation.

P.S. First and foremost while testing developmental releases do not blindly accept "partial updates"!  Read appropriate sticky.

OK, I didn't realize that, I will be very careful. How do I know if it is a partial update?

---

### Post by garvinrick4 on 2010-06-28
If you use your GUI update manager it will tell you that you are about to do partial upgrades, just say no.
 Use the command line:
```
sudo apt-get update && sudo apt-get upgrade
```If you want to stick to 10.10 maverick meerkat then download an .iso file and BURN it to a disc.
It will then be ready to reinstall if it gets mucked up by upgrades or user. One thing is you will get fast at setting up your GUI.

[Ubuntu 10.10 (Maverick Meerkat) Daily Build]("http://cdimage.ubuntu.com/daily/current/")

---

### Post by arpanaut on 2010-06-28
^^^what he said^^^

AND:
[http://ubuntuforums.org/showthread.php?t=1479146](http://ubuntuforums.org/showthread.php?t=1479146)

for more information.

---

### Post by joelw135 on 2010-06-28
> **garvinrick4 said:**
> If you use your GUI update manager it will tell you that you are about to do partial upgrades, just say no.
 Use the command line:
```
sudo apt-get update && sudo apt-get upgrade
```If you want to stick to 10.10 maverick meerkat then download an .iso file and BURN it to a disc.
It will then be ready to reinstall if it gets mucked up by upgrades or user. One thing is you will get fast at setting up your GUI.

[Ubuntu 10.10 (Maverick Meerkat) Daily Build]("http://cdimage.ubuntu.com/daily/current/")

Thanks for the info. I will say know and use the terminal commands as directed.

---

