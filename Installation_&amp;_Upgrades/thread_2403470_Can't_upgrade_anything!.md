---
title: "Can't upgrade anything!"
date: 2018-10-11
forum: Installation &amp; Upgrades
---

### Post by timswait on 2018-10-11
I'm running 17.10 and want to upgrade to 18.04, but I'm not being offered the option. I have setting in Muon Package manager to tell me about upgrades, but I'm not being offered it. So I tried to upgrade by command prompt but that also doesn't work:
```
mt1tjs@mt1tjs-Precision-M4600:~$ lsb_release -a
LSB Version:    core-9.20160110ubuntu5-amd64:core-9.20160110ubuntu5-noarch:security-9.20160110ubuntu5-amd64:security-9.20160110ubuntu5-noarch
Distributor ID: Ubuntu
Description:    Ubuntu 17.10
Release:        17.10
Codename:       artful
mt1tjs@mt1tjs-Precision-M4600:~$ sudo apt-get update
Hit:1 http://gb.archive.ubuntu.com/ubuntu artful InRelease
Hit:2 http://gb.archive.ubuntu.com/ubuntu artful-updates InRelease      
Hit:3 http://archive.canonical.com artful InRelease                     
Hit:4 http://gb.archive.ubuntu.com/ubuntu artful-backports InRelease    
Hit:5 http://gb.archive.ubuntu.com/ubuntu artful-security InRelease
Reading package lists... Done
mt1tjs@mt1tjs-Precision-M4600:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
mt1tjs@mt1tjs-Precision-M4600:~$ sudo apt dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.

```

It's also seems wrong that it can't find anything to update as I haven't installed any updates in ages, I'm sure there must be some out there! It seems it just isn't checking properly, but I can't see anything wrong with my software sources and it's not giving any error messages. It doesn't take very long to do the apt-get update command, it doesn't really seem to be downloading anything.

---

### Post by wildmanne39 on 2018-10-11
Hello, you can not update because 17.10 is no longer supported it has reached EOL, the repositories have been removed, your best option is to backup your important data and do a clean install.

---

### Post by timswait on 2018-10-11
But it's only one version behind the current one?! Is there really no way from the last version to the current one?

---

### Post by wildmanne39 on 2018-10-11
It will be much more painful but you can try the following:

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by Holger_Gehrke on 2018-10-11
'apt-get update' and 'apt-get upgrade' only upgrade packages within the same release. If they don't give you errors about not finding a 'Release'-file, then 'artful' hasn't ***yet*** been removed from the servers and put in the archive. There haven't been any updates to 17.10 since July, when it went out of support, so if you ran update/upgrade since then your system is as up to date as it's going to get. For doing an upgrade from one release to the next you don't use 'apt' or 'apt-get' but 'do-release-upgrade'. For a recently EOL system that hasn't yet been moved to the 'old-releases' server, doing 'sudo apt-get update', 'sudo apt-get dist-upgrade' followed by 'sudo do-release-update' should do it. Don't forget to do a backup before upgrading, it's not good to give Murphy's Law an additional opportunity to strike.

Holger

---

### Post by timswait on 2018-10-12
That doesn't find anything
```

mt1tjs@mt1tjs-Precision-M4600:~$ sudo do-release-upgrade
[sudo] password for mt1tjs: 
Checking for a new Ubuntu release
No new release found.
mt1tjs@mt1tjs-Precision-M4600:~$

```
Actually, now I remember, I did try this earlier in the year, soon after 18.04 first came out, before support for 17.10 ended and it didn't find the new release then. The update manager has NEVER told me that there's a new release available. So the problem of it not being able to find the newer release isn't to do with 17.10 being unsupported, it predated that.

---

### Post by Impavidus on 2018-10-12
The update manager must be set to check for release upgrades. Check here:```
cat /etc/update-manager/release-upgrades
```If it says "never", change it to "normal". It's a bit late now, but upgrading may still work.

---

### Post by timswait on 2018-10-12
It's set to Prompt=normal and always has been, but it didn't prompt me!

---

