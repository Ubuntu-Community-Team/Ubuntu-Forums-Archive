---
title: "Custom Application Settings on OS upgrade"
date: 2021-07-12
forum: Installation &amp; Upgrades
---

### Post by erosman on 2021-07-12
From what I have gathered, when OS gets updated (e.g. 20 -> 21), all applications have to be reinstalled. What happens to custom application settings?
Are they lost or are they saved elsewhere?

---

### Post by Holger_Gehrke on 2021-07-12
User-specific settings for applications are stored separately for each user in files in the user's home-directory. So depending on the way you have setup your system and the way you do the upgrade, the procedure to keep your settings varies slightly. If you do an upgrade by 'do-release-upgrade' your settings (and any applications you've installed from the official repositories which are also available for the newer version) will be good after the upgrade. If you do an upgrade by clean install of the new version and have your home directory on a separate partition you can tell the installer to use the existing partition for '/home' and not to format it. While you will lose applications that way, your settings - even for applications that you need to install again - are save. If you've originally installed everything in one partition and do an upgrade by clean install, then you have to backup your home directory and restore it afterwards.

Holger

---

### Post by grahammechanical on 2021-07-12
The Ubuntu default applications are upgraded along with the Ubuntu operating system. When doing an online upgrade it is best to take the OS back to the default situation as much as possible. 

Any Personal Package Archives (PPA) should be disabled. Applications installed through a PPA will not be removed but they may not work if the developer has not upgraded them to work with the new version of Ubuntu. 

An online Upgrade does not format any partitions. Over time an OS can get cluttered. This is why some of us prefer a fresh install. Either that or we stay on an LTS version. Ubuntu 20.04 is an Long Term Support version. Ubuntu 21.04 is not LTS. Best to wait until Ubuntu 22.04 LTS is released and either fresh install with the conditions mentioned in an earlier post or do an online upgrade.  But backup personal files and important data.

Regards


Regards

---

### Post by monkeybrain20122 on 2021-07-12
If you have a separate home partition then all your user config will be preserved (unless you do some customization/optimization in the system files, those of course will be wiped out) But if you have a lot of tweaks chances are some old configs won't apply after a system unpdate and may result in corruption. So if you have a lot of customized config files I would just save the ~/.config folder and possibly something in ~/.local/share along with some app's configurations which are not in the above (e.g ~/.mozilla) and then after updating your OS restore those on a case by case basis, that way, if something goes wrong you know exactly what causes it. I know this is long winded but probably safest.

Also "upgrade" is more likely to be successful if your system is pristine, i.e, without much customization. But in that case why not do a clean install? And if you have a lot of customized tweaks "upgrade" will likely fail, again you should do a clean install. So IMO a fresh install either way.

---

