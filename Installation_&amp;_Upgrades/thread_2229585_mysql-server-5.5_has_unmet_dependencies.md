---
title: "mysql-server-5.5 has unmet dependencies"
date: 2014-06-14
forum: Installation &amp; Upgrades
---

### Post by alaajabre on 2014-06-14
[COLOR=#333333][FONT=UbuntuRegular]Every time I open the software center I get this message:[/FONT][/COLOR]
[INDENT]Item can not be installed or removed until package catalog is repaired
[/INDENT][COLOR=#333333][FONT=UbuntuRegular]I click repair then I get[/FONT][/COLOR]
[INDENT]Package operation failed
[/INDENT][COLOR=#333333][FONT=UbuntuRegular]I tried to remove mysql-server-5.5 using terminal sudo apt-get --purge remove mysql-server-5.5and I got this message:[/FONT][/COLOR]
[INDENT]The following packages have unmet dependencies: mysql-server : Depends: mysql-server-5.5 but it is not going to be installed"
[/INDENT][COLOR=#333333][FONT=UbuntuRegular]I got the same message when tried to install it. I'm running Ubuntu 12.04[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I tried: sudo apt-get remove mysql-sever and I got this:[/FONT][/COLOR]
[INDENT]dpkg: error processing mysql-server-5.5 (--configure): subprocess installed post-installation script returned error exit status 1
[/INDENT][COLOR=#333333][FONT=UbuntuRegular]then the system has sent me a message that this is a [bug]("https://bugs.launchpad.net/ubuntu/+source/mysql-5.5/+bug/1311925")

is there a work around for this problem?[/FONT][/COLOR]

---

### Post by nerdtron on 2014-06-14
```
apt-get install -f mysql-server
```

Doesn't work?
Try the following but be sure that all mysql processes were stopped or killed.

```
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get remove --purge mysql-client-5.5 mysql-client-core-5.5 mysql-common mysql-server mysql-server-5.5 mysql-server-core-5.5
sudo apt-get install mysql-server
```

Still doesn't work?
[http://ubuntuforums.org/showthread.php?t=1998260&page=4](http://ubuntuforums.org/showthread.php?t=1998260&page=4)

---

### Post by alaajabre on 2014-06-14
Solved thank you very much

---

### Post by mörgæs on 2014-06-14
Good, then please mark the thread so.

---

