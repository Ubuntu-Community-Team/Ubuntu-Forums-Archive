---
title: "Upgrading server from 9.04 to 10.04 , retaining the applications"
date: 2011-12-17
forum: Installation &amp; Upgrades
---

### Post by deepakdeshp on 2011-12-17
I have Ubuntu 9.04 server , 64 bit, which I want to upgrade to 10.04. I have loaded and configured lot of applications on this server like Nagios etc. Installing fresh from cd , I may be losing all these applications and configurations. 


[LIST=1]
[*]Is there any way to upgrade to 10.04 yet retain all my applications which are running on 9.04?
[*]Is there any way I can convert the 64 bit os to 32 bit distribution after I upgrade to 10.04 64 bit ?
[/LIST]

---

### Post by BC59 on 2011-12-17
If you upgrade, theoretically you don't loose your data and your applications. 
The problem is that upgrading is riskier than a fresh install.

Look here how to upgrade:
[http://ubuntuforums.org/showthread.php?t=1469248](http://ubuntuforums.org/showthread.php?t=1469248)
[http://echenh.blogspot.com/2010/04/how-to-upgrade-ubuntu-server-904-to-910.html](http://echenh.blogspot.com/2010/04/how-to-upgrade-ubuntu-server-904-to-910.html)
[http://www.sucka.net/2010/04/upgrade-ubuntu-server-to-10-04-lts/](http://www.sucka.net/2010/04/upgrade-ubuntu-server-to-10-04-lts/)

You can convert your system from 64bit to 32bits, but as you said you are going to loose all your applications, because you have to reinstall them to fit in the new architecture.

---

### Post by deepakdeshp on 2011-12-17
> If you upgrade, theoretically you don't loose your data and your applications. 
The problem is that upgrading is riskier than a fresh install.
.
But I do not want to loose my data and my applications  but at the same time want to upgrade to 10.04 from 9.04.

---

### Post by BC59 on 2011-12-17
Yes but there is always a risk to have a failed installation.

---

### Post by oldos2er on 2011-12-17
> **deepakdeshp said:**
> But I do not want to loose my data and my applications  but at the same time want to upgrade to 10.04 from 9.04.

You would need to go from 9.04 to 9.10 to 10.04, which will be tricky because 9.10 is EOL. See [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

If it were my system, I'd backup everything and run a fresh install of 10.04.

---

### Post by deepakdeshp on 2011-12-17
You are right. I have taken backup and started the upgrade. I will surely report what happens. I am using the 2nd link which you gave. At least the packages are being downloaded now, which wasnt happening previously.

But there are also many not found error messages also when I am upgrading from 9.04 to 9.10

---

