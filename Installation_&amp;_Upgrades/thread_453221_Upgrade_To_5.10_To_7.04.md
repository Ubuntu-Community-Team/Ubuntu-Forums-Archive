---
title: "Upgrade To 5.10 To 7.04"
date: 2007-05-24
forum: Installation &amp; Upgrades
---

### Post by ahsanghalib on 2007-05-24
Hi, I am new user to Ubuntu Even in Linux. So, I requested the CD's of Ubuntu 7.04 that I received but the Installation is very bad. even if we click after the Install icon after booting from CD. but the installation not running properly. it held my system. I have P4 with 256MB Ram and 40 GB of harddisk Intel Board. so i install the ubuntu 5.10 now i want to upgrade it into ubuntu 7.04 please tell me the way and also why the installation is not running well. 

MUHAMMAD AHSAN
[email]ahsanghalib@gmail.com[/email]
+923027350315

---

### Post by Steven_B on 2007-05-24
Ubuntu 5.10 (Breezy)?  Do you mean 6.10 (Edgy - released last October)?
To upgrade open a terminal, and type ```
gksudo update-manager -c
```  After typing in your password, you should get a window with the notice "new distribution release 'dapper/edgy/feisty' is available.  Click upgrade, and follow the instructions.

Look here for a more complete guide.
[http://daniel.holba.ch/blog/?p=14]("http://daniel.holba.ch/blog/?p=14")

You will have to upgrade through each release.  If you're on Breezy, you'll go from Breezy to Dapper, from Dapper to Edgy, and then from Edgy to Feisty.
The process is the same for each upgrade.  If you haven't made a lot of changes to your system, the upgrade should be relatively simple.

By "held your system", do you mean crashed, or ran really slowly?  The Live CD runs much slower than a normal installation, even on a fast computer.  Could you give us some more details of what is happening?

---

### Post by hellmet on 2007-05-24
Ubuntu's cds have always had problems with some or the other architecture. It maybe the flipside of having the bleeding edge tech. on your system. If the Feisty Live cd did not work, do try the Alternate Cd as it has had a better success rate on problematic systems.

Upgrading from 5.10 to 7.04 is not recommended as its many releases away. You'd have to upgrade to each next release until you reach Feisty as there isn't a direct way of upgrading to the latest version.

---

### Post by Claus7 on 2007-05-24
Hello,

In order to upgrade you have to do it gradually from one version to the other. In other words you have to go from 5.10 to 6.06 then to 6.10 and finally to 7.04. Or you format your disk and have a brand new 7.04 installation.

Regards!

---

