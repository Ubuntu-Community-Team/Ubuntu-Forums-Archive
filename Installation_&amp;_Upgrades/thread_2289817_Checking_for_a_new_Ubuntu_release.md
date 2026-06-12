---
title: "Checking for a new Ubuntu release"
date: 2015-08-07
forum: Installation &amp; Upgrades
---

### Post by xoylo on 2015-08-07
Hello everyone,i am new user ubuntu :D
&#304; Try every found command,i can't fixed..
i wanna 12.04 update 14.04

root@xaylo-Inspiron-3542:/home/xaylo# sudo do-release-upgrade
Checking for a new Ubuntu release
No new release found

root@xaylo-Inspiron-3542:/home/xaylo# cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.5 LTS"


and i changed sources.list [http://ubuntuforums.org/showthread.php?t=2218324](http://ubuntuforums.org/showthread.php?t=2218324)

---

### Post by robbie 348 on 2015-08-07
I think if you open update manager there should be an update option on there.

---

### Post by xoylo on 2015-08-07
yes,me too thought =D

[IMG]http://i.hizliresim.com/3aYo10.png[/IMG]

---

### Post by grahammechanical on 2015-08-07
Click the button that says "Settings." Then go to the Updates tab and look at the drop down menu for the panel called: Notify me of a new Ubuntu version. There are three settinsg. Any new version; for long tem support versions & never. You need the setting: for long term support versions.

---

### Post by Bucky Ball on 2015-08-07
Software and Updates> Updates tab> set 'notify me of LTS releases' at the bottom option> close. That will update and show you there is a new LTS release available. Accept.

Before doing the upgrade disable any PPAs you have installed manually from third-parties.

---

### Post by deadflowr on 2015-08-07
Alternatively if you where to want to change the setting manually, you can edit the file:
*/etc/update-manager/release-upgrades*
and change the line that has prompt= from whatever it says, to prompt=lts.

Be aware that which ever method to change the settings you choose you need to do either a check(in the update manager)
or run apt-get update (from the command line)
So that the updated settings can take affect.
12.04's update manager might ignore the change at first and not do an automatic reload/update.

Sidenote: since you are running this as root, no need for sudo.

Also, funny thing is do-release-upgrade command actually doesn't require sudo to work.
(It'll ask for your password eventually, but will start and run initially without it.)


Just a couple of thoughts, anyway...

---

