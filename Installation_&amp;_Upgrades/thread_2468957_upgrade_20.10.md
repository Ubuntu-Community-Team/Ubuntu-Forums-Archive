---
title: "upgrade 20.10"
date: 2021-11-15
forum: Installation &amp; Upgrades
---

### Post by Aikane on 2021-11-15
Hey!
My ubuntu 20.10 is no longer supported.
When trying to upgrade 21.04. I get the the result below.
Anyone who can help me how get on with the upgrade? 
Thomas

[I]sudo do-release-upgrade.   
Your Ubuntu release is no longer supported.
Install all available updates for your version before upgrading.
0 to upgrade, 0 to reinstall, 0 to remove and 1 not to upgrade.$ sudo apt update 

thomas@Kontor:~$ sudo apt update
Bra:1 [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) groovy InRelease
Bra:2 [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) groovy-updates InRelease
Bra:3 [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) groovy-backports InRelease
Bra:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) groovy-security InRelease              
Bra:5 [https://packages.microsoft.com/repos/ms-teams](https://packages.microsoft.com/repos/ms-teams) stable InRelease           
Reads package lists… Done                           
Builds dependency trees  
Reads condition information… Done
1 package can be upgraded. Run "apt list --upgradable" to see it.          

thomas@Kontor:~$ apt list --upgradable
Lists… Done
dh-python/groovy,groovy 4.20200925 all [upgradeable from: 4.20191017ubuntu7]
N: There is 1 additional version. Use the "-a" switch to see it.[/I]

---

### Post by ActionParsnip on 2021-11-15
If you switch to the main repository does it help?

---

### Post by Dennis N on 2021-11-15
In Software & Updates tool, Updates Tab, be sure you have set "Notify me of a new Ubuntu version" to "For any new version".
Run Software Updater.
You get an "Updates Unavailable" notice. But, you are allowed to update to the next supported release which for 20.10 is 21.04 at this time.
You should see an "Upgrade" Button.  (see attached screenshot)
Click "Upgrade"
Upgrade should begin.
It doesn't matter if your 20.10 is up to date or not. I don't believe mine was. That is my experience.
Note: This particular upgrade was done on Oct 23, 2021 and Ubuntu 20.10 was long past end of support. The situation now (Nov 15) has not changed.

---

### Post by Aikane on 2021-11-16
Switch to main repository does not change anything.:sad:

Software and update tool is set to "Notify me of a new Ubuntu version" to "For any new version".

Running software updater: 
*   -- Software updates are no longer provided for Ubuntu 2010*
[I]   -- To increase security, you should upgrade to Ubuntu 21.04

 [/I]Everything ok so far, but when clicking upgrade, nothing happens!???

---

### Post by Impavidus on 2021-11-16
It appears to be unwilling to upgrade dh-python to the latest version. Maybe find out why:```
sudo apt upgrade dh-python
```
Alternatively, as version 21.10 is already released, you could avoid two release upgrades by just installing 21.10. That's the quick solution.

---

### Post by oldos2er on 2021-11-18
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

